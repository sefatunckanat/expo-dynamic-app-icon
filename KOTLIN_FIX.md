# Kotlin Compatibility Fix

## Problem
When adding this module to an Expo project, you may encounter a Kotlin version compatibility error:

```
Module was compiled with an incompatible version of Kotlin. 
The binary version of its metadata is 2.1.0, expected version is 1.9.0.
```

## Solution

### Changes Made

1. **Updated `expo-modules-core` dependency** (package.json)
   - Changed from `^2.1.1` to `^3.0.0`
   - Version 3.x supports Kotlin 2.0+ which is required by newer Expo and React Native versions

2. **Updated Kotlin compiler options** (android/build.gradle)
   - Added explicit Kotlin compiler configuration to ensure JVM 11 target compatibility
   - This ensures the module compiles with the same Kotlin version as your Expo project

### Installation

After these changes, install the module in your Expo project:

```bash
npm install @g9k/expo-dynamic-app-icon
# or
pnpm install @g9k/expo-dynamic-app-icon
# or
yarn add @g9k/expo-dynamic-app-icon
```

### For Local Development

If you're developing this module locally:

1. Install dependencies:
```bash
pnpm install
```

2. Rebuild the module:
```bash
pnpm run build
```

3. Link to your project:
```bash
cd your-expo-project
npm install /path/to/expo-dynamic-app-icon
```

### Compatibility

- ✅ Expo SDK 52+
- ✅ React Native 0.74+
- ✅ Kotlin 2.0+
- ✅ Android Gradle Plugin 8.x

## Testing

After installation, rebuild your Android app:

```bash
expo prebuild --clean
expo run:android
```

If you still encounter issues, try:

```bash
cd android
./gradlew clean
cd ..
expo run:android
```

