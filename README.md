# YESAnrDetector
<p align="center">
    <img src="https://img.shields.io/badge/Swift-5.0-orange.svg" />
    <img src="https://img.shields.io/badge/protspace-Twitter%3A%20%40protspace-green.svg" alt="Twitter: @protspace" />
</p>

ANRDetector - is a simple framework for detecting cases when application is not responsive (Main thread is blocked).
Using a timer it measures how much time was spend on a test operation. It notifies about changes within delegate pattern.

## Usage
1. Drag-and-drop Framework/ANRDetector.framework to your project. Make sure it is present under ‘Link binary with libraries” section in Build Phases of your project.
2. Import ANRDetector in your class 
```swift
import ANRDetector
```

3. Implement delegate methods (if needed)
	
```swift
extension YourClass: ANRDetectorDelegate {

        func didDetectANR() {
            print("⛔️ ANR DETECTED")
        }

        func didBackToNormal(anrDuration: TimeInterval) {
            print("✅ Back to normal. ANR duration: \(anrDuration) sec.")
        }
}
```

Problems/difficulties I’ve met:

1. The ANR duration time calculated is not very precise - this could be improved.
2. Preparing universal framework that supports x86_64 / arm64 (lipo). I wish there were simple checkbox for this.
