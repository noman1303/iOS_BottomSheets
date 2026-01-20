# 📱 SwiftUI Bottom Sheets Showcase

A comprehensive SwiftUI project demonstrating 12 different bottom sheet patterns commonly used in modern iOS applications. Built with clean architecture, reusability, and practical UI patterns for options, forms, filters, pickers, and quick actions.

![Swift](https://img.shields.io/badge/Swift-5.9-orange.svg)
![Platform](https://img.shields.io/badge/Platform-iOS%2013.0+-lightgrey.svg)
![SwiftUI](https://img.shields.io/badge/SwiftUI-3.0+-blue.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

---

## 🎯 Project Overview

This project serves as a complete reference for implementing bottom sheets in SwiftUI, covering both system-provided and custom-designed sheets with modern iOS design patterns.

### Goals
- ✅ Understand how bottom sheets work in SwiftUI
- ✅ Learn when and why to use each type
- ✅ Build reusable, scalable UI components
- ✅ Prepare for real-world iOS development and interviews

---

## 📋 Bottom Sheets Implemented

### Original Sheets (5)

| # | Sheet Name | Description | Use Case |
|---|------------|-------------|----------|
| 1 | **OptionsSheetView** | OK / Cancel confirmation | Quick confirmations |
| 2 | **FormSheetView** | User form (Name & Email) | Data entry without navigation |
| 3 | **FilterSheetView** | Price slider & availability toggle | E-commerce filtering |
| 4 | **QuickActionSheetView** | Quick actions (Share, Save, Delete) | Fast contextual actions |
| 5 | **ConfirmationDialog** | Native iOS action dialog | System-level confirmations |

### Additional Sheets (7)

| # | Sheet Name | Description | Use Case |
|---|------------|-------------|----------|
| 6 | **SettingsSheetView** | App settings with toggles | User preferences |
| 7 | **ShareSheetView** | Share options with icons | Content sharing |
| 8 | **SortSheetView** | Sort selection with checkmarks | List organization |
| 9 | **PickerSheetView** | Segmented & wheel pickers | Multi-option selection |
| 10 | **FeedbackSheetView** | Star rating & feedback form | User reviews |
| 11 | **DatePickerSheetView** | Date & time picker | Scheduling & bookings |
| 12 | **ListSelectionSheetView** | Multi-select list | Batch operations |

---

## 🏗 Project Structure

```
BottomSheetsSwiftUI/
├── BottomSheetsSwiftUIApp.swift
├── ContentView.swift
└── Sheets/
    ├── OptionsSheetView.swift
    ├── FormSheetView.swift
    ├── FilterSheetView.swift
    ├── QuickActionSheetView.swift
    ├── SettingsSheetView.swift
    ├── ShareSheetView.swift
    ├── SortSheetView.swift
    ├── PickerSheetView.swift
    ├── FeedbackSheetView.swift
    ├── DatePickerSheetView.swift
    └── ListSelectionSheetView.swift
```

---

## ⚙️ How It Works

### 1. Entry Point

```swift
@main
struct BottomSheetsSwiftUIApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
```

The app starts with `ContentView` as the root view.

### 2. Main Navigation (ContentView)

Each bottom sheet is controlled using dedicated `@State` properties:

```swift
@State private var showFilter = false

// Button to trigger sheet
Button("Filter Bottom Sheet") {
    showFilter = true
}

// Sheet presentation
.sheet(isPresented: $showFilter) {
    if #available(iOS 16.0, *) {
        FilterSheetView()
            .presentationDetents([.medium, .large])
            .presentationDragIndicator(.visible)
    } else {
        FilterSheetView()
    }
}
```

---

## 🧠 Key SwiftUI Concepts

### @State
Local UI state management that automatically triggers view updates.

```swift
@State private var isPresented = false
```

### .sheet Modifier
Presents bottom sheets with automatic handling of presentation and dismissal.

```swift
.sheet(isPresented: $showForm) {
    FormSheetView()
}
```

### .presentationDetents (iOS 16+)
Controls sheet height with expandable options.

```swift
.presentationDetents([.medium, .large])
```

**Note:** Fallback logic is implemented for iOS 15 and below.

### @Environment(\.dismiss)
Modern way to dismiss sheets from within the presented view.

```swift
@Environment(\.dismiss) var dismiss

Button("Close") {
    dismiss()
}
```

---

## 🎨 Featured Sheet Implementations

### Options Sheet
```swift
Button("OK") {
    dismiss()
}
```
**Use Case:** Quick confirmations, simple choices

### Form Sheet
```swift
TextField("Name", text: $name)
TextField("Email", text: $email)
```
**Use Case:** Data entry, user registration

### Filter Sheet
```swift
Toggle("Available Only", isOn: $isAvailable)
Slider(value: $price, in: 0...100)
```
**Use Case:** E-commerce filtering, search refinement

### Quick Action Sheet
```swift
Button("Delete") {
    // Action
}
.foregroundColor(.red)
```
**Use Case:** Fast actions, destructive operations

### Date Picker Sheet
```swift
DatePicker("Select Date", 
    selection: $selectedDate,
    displayedComponents: .date
)
.datePickerStyle(.graphical)
```
**Use Case:** Scheduling, booking flows, reminders

### List Selection Sheet
```swift
List(items, id: \.self) { item in
    HStack {
        Text(item)
        Spacer()
        if selectedItems.contains(item) {
            Image(systemName: "checkmark")
        }
    }
}
```
**Use Case:** Multi-selection, batch operations

---

## 🎯 Design Principles

- ✅ **Single Responsibility**: Each sheet has one clear purpose
- ✅ **Reusability**: Components can be easily reused across projects
- ✅ **Declarative UI**: Pure SwiftUI with no UIKit dependencies
- ✅ **Responsive Design**: Works on all iPhone and iPad sizes
- ✅ **Version Compatibility**: Graceful degradation for older iOS versions

---

## 📱 iOS Version Compatibility

| Feature | Minimum iOS Version |
|---------|-------------------|
| `.sheet` | iOS 13.0+ |
| `.confirmationDialog` | iOS 15.0+ |
| `.presentationDetents` | iOS 16.0+ |
| `@Environment(\.dismiss)` | iOS 15.0+ |

All features include availability checks and fallbacks where necessary.

---

## 🚀 Getting Started

### Requirements
- Xcode 14.0+
- iOS 13.0+
- Swift 5.9+

### Installation

1. Clone the repository
```bash
git clone https://github.com/yourusername/BottomSheetsSwiftUI.git
```

2. Open the project
```bash
cd BottomSheetsSwiftUI
open BottomSheetsSwiftUI.xcodeproj
```

3. Build and run
- Select your target device or simulator
- Press `Cmd + R` to run
 
