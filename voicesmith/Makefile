.PHONY: jni

default: help

help:
	@echo "make jni:             Generate JNI headers"
	@echo "make build[-verbose]: Build JNI sources"
	@echo "make release:         Make release APK"
	@echo "make install:         Install released APK"
	@echo "make uninstall:       Uninstall released APK"
	@echo "make start:           Start main activity"
	@echo "make clean:           Clean build/release files"

jni:
	jni/GenerateHeaders.sh \
		"Math" \
		"de.jurihock.voicesmith.dsp" \
		"de/jurihock/voicesmith/dsp" \
		"Math"
	jni/GenerateHeaders.sh \
		"KissFFT" \
		"de.jurihock.voicesmith.dsp" \
		"de/jurihock/voicesmith/dsp" \
		"KissFFT"
	jni/GenerateHeaders.sh \
		"NativeResampleProcessor" \
		"de.jurihock.voicesmith.dsp.processors" \
		"de/jurihock/voicesmith/dsp/processors" \
		"Processors"
	jni/GenerateHeaders.sh \
		"NativeTimescaleProcessor" \
		"de.jurihock.voicesmith.dsp.processors" \
		"de/jurihock/voicesmith/dsp/processors" \
		"Processors"

build:
	ndk-build

build-verbose:
	ndk-build V=1

release:
	ant release

install:
	adb install bin/Voicesmith-release.apk

uninstall:
	adb uninstall de.jurihock.voicesmith

start:
	adb shell am start -n de.jurihock.voicesmith/.activities.HomeActivity

clean:
	ndk-build clean && rm -rfv libs obj
	ant clean
