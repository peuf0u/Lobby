# Lobby

An iOS navigation concept built with `UIStackView`. The menu is a stack of full-width rows. Tap one and it springs open to fill the screen while the others collapse. The menu button brings them all back.

| Cards | Blur |
|:---:|:---:|
| <img src="docs/cards.gif" width="266" alt="Colored rows; tapping one expands it to full screen"> | <img src="docs/blur.gif" width="268" alt="Titles over a blurred photo; tapping one clears the blur and keeps only that title"> |

Read the write-up: [Adopting UIStackView](https://medium.com/@potocek.patrik/adopting-uistackview-fe330577d8d2) on Medium.

## How it works

- [`CustomStackView.swift`](NavigationConcept/CustomStackView.swift) subclasses `UIStackView` and adds a tap gesture to every arranged subview. A `StackViewDelegate` reports which index was tapped, since the stack view can't do that itself.
- [`CardsLobbyViewController.swift`](NavigationConcept/CardsLobbyViewController.swift) maps that index to a `LobbyScreen` and, inside one spring animation, hides every other row and moves the stack's top constraint. The stack view recalculates its Auto Layout constraints, so the chosen row grows to full height.
- [`BlurLobbyViewController.swift`](NavigationConcept/BlurLobbyViewController.swift) does the same over a background photo and fades out the blur and the other titles too.

Written in Swift 3 for iOS 9.
