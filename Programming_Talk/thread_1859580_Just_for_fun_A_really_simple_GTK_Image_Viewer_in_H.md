---
title: "Just for fun: A really simple GTK Image Viewer in Haskell"
date: 2011-10-14
forum: Programming Talk
---

### Post by satsujinka on 2011-10-14
As the thread says, a simple image viewer written in haskell. Comments and questions are welcome. If people are interested I'll update with more features.

```
module Main where

import Data.Char
import Graphics.UI.Gtk
import IO
import System
import System.Directory
import Text.Regex.Posix
import Data.IORef

main = do
    initGUI
    window <- windowNew
    onDestroy window mainQuit
    scroll <- scrolledWindowNew Nothing Nothing
    scrolledWindowSetPolicy scroll PolicyAutomatic PolicyAutomatic
    vbox <- vBoxNew False 0
    hbox <- hBoxNew False 0
    set window [windowDefaultWidth := 600, windowDefaultHeight := 500,
                containerChild := vbox, containerBorderWidth := 0]
    image <- imageNew
    quit <- buttonNewFromStock stockQuit
    quitID <- on quit buttonActivated $ do mainQuit
    nextButton <- buttonNewFromStock stockGoForward
    backButton <- buttonNewFromStock stockGoBack
    boxPackStart hbox backButton PackRepel 0
    boxPackStart hbox nextButton PackRepel 0
    boxPackEnd hbox quit PackRepel 0
    boxPackEnd vbox hbox PackNatural 0
    boxPackStart vbox scroll PackGrow 0
    scrolledWindowAddWithViewport scroll image
    args <- getArgs
    imageLst <- dirContents args
    imageSetFromFile image (head imageLst)
    position <- newIORef 0
    on nextButton buttonActivated $ do
        oldPosition <- readIORef position
        if oldPosition < (length imageLst)-1
            then writeIORef position (1+oldPosition)
            else writeIORef position 0
        newPosition <- readIORef position
        imageSetFromFile image (imageLst !! newPosition)
    on backButton buttonActivated $ do
        oldPosition <- readIORef position
        if (oldPosition > 0)
            then writeIORef position (oldPosition-1)
            else writeIORef position ((length imageLst)-1)
        newPosition <- readIORef position
        imageSetFromFile image (imageLst !! newPosition)
    widgetShowAll window
    mainGUI

dirContents [] = do
    cwd <- getCurrentDirectory
    lst <- getDirectoryContents cwd
    let flst = filter isImage lst in
        if flst == [] then error "No images"
        else return flst
dirContents (x:xs) = do
    cwd <- getCurrentDirectory
    lst <- getDirectoryContents cwd
    let flst = filter isImage lst in
        if flst == [] then error "No images"
        else
            if elem x flst
                then return (shift x flst)
                else return flst

isImage :: String -> Bool
isImage filename = let pattern = "(.png|.jpg|.gif|.bmp|.jpeg)" in
    filename =~ pattern :: Bool

shift :: String -> [String] -> [String]
shift item lst@(x:xs) = if item == x then lst else shift item (xs++[x])

```

---

### Post by nvteighen on 2011-10-14
Looks interesting. What are the dependencies besides Haskell, of course? (e.g. I haven't been able to find that POSIX Regex package on the Debian repos).

---

### Post by Bachstelze on 2011-10-14
> **nvteighen said:**
> Looks interesting. What are the dependencies besides Haskell, of course? (e.g. I haven't been able to find that POSIX Regex package on the Debian repos).

If you are not strapped for space, install haskell-platform. :) Otherwise the specific package is libghc-regex-posix-dev.

*EDIT:* Apparently it's not in Debian stable, though...

---

### Post by nvteighen on 2011-10-14
> **Bachstelze said:**
> If you are not strapped for space, install haskell-platform. :) Otherwise the specific package is libghc-regex-posix-dev.

*EDIT:* Apparently it's not in Debian stable, though...

Oh, thanks. I'm on Debian testing, so no problem here :)

Hey, very nice program. I'll study it a bit: I'm interested on how to do GUIs in a language like Haskell :)

---

### Post by cgroza on 2011-10-14
Really interesting. I have just started to explore GUI programming in functional languages too. Currently, I have only tried wxHaskell, still trying to find something appropriate for OCaml.

---

### Post by satsujinka on 2011-10-15
@nvteighen
The Text.Regex.Posix package should be in the default. At least, on Arch it is (I can take a look on an Ubuntu install shortly though.)
Other than base packages, you'll also need to have Gtk2hs installed, which is simply the GTK+ wrapper for haskell.

@cgroza
You should post some wxhaskell code, so we can compare and contrast approaches. Especially since wxhaskell just uses GTK+ anyways.

---

### Post by cgroza on 2011-10-15
> **satsujinka said:**
> 
@cgroza
You should post some wxhaskell code, so we can compare and contrast approaches. Especially since wxhaskell just uses GTK+ anyways.
Sure. wxHaskell uses GTK+ because wxWidgets itself wraps GTK+ on Linux.

---

### Post by satsujinka on 2011-10-15
UPDATE: 
New Feature: Fit Image to Window.
Notes: Behaves the way you'd expect except with gif files. For the moment gif files will always display at their actual size. This is due to the fact that gif files can be animations and there's no easy way to modify an animation's size. I could detect if the gif is static and re-open the gif as a standard pixbuf but it's a dozen lines of code or so to do that. When I refactor the creation of buttons and assigning events to them, I'll add in code to detect static gif files.

```
module Main where

import Data.Char
import Graphics.UI.Gtk
import IO
import System
import System.Directory
import Text.Regex.Posix
import Data.IORef

main = do
    initGUI
    window <- windowNew
    onDestroy window mainQuit
    scroll <- scrolledWindowNew Nothing Nothing
    scrolledWindowSetPolicy scroll PolicyAutomatic PolicyAutomatic
    vbox <- vBoxNew False 0
    hbox <- hBoxNew False 0
    set window [windowDefaultWidth := 600, windowDefaultHeight := 500,
                containerChild := vbox, containerBorderWidth := 0]
    image <- imageNew
    quit <- buttonNewFromStock stockQuit
    quitID <- on quit buttonActivated $ do mainQuit
    nextButton <- buttonNewFromStock stockGoForward
    backButton <- buttonNewFromStock stockGoBack
    scaleToggle <- toggleButtonNewWithLabel "Fit to Window"
    boxPackStart hbox backButton PackRepel 0
    boxPackStart hbox nextButton PackRepel 0
    boxPackEnd hbox quit PackRepel 0
    boxPackEnd hbox scaleToggle PackRepel 0
    boxPackEnd vbox hbox PackNatural 0
    boxPackStart vbox scroll PackGrow 0
    scrolledWindowAddWithViewport scroll image
    args <- getArgs
    imageLst <- dirContents args
    imageSetFromFile image (head imageLst)
    expand <- newIORef True --Used for deciding whether an image should be fullsize
    position <- newIORef 0
    on scaleToggle toggled $ do
        pos <- readIORef position
        let gifPattern = ".gif"
            filename = (imageLst !! pos) in
                if filename =~ gifPattern :: Bool
                    then imageSetFromFile image filename--possibly an animation, Ignores Scaling
                    else do --Static Image, Scale away!
                        exp <- readIORef expand
                        if exp then do
                            writeIORef expand False
                            windowSize <- windowGetSize window
                            pix <- pixbufNewFromFileAtScale filename ((fst windowSize)-10) ((snd windowSize)-32) True
                            imageSetFromPixbuf image pix
                        else do
                            writeIORef expand True
                            imageSetFromFile image filename
    on nextButton buttonActivated $ do
        oldPosition <- readIORef position
        if oldPosition < (length imageLst)-1
            then writeIORef position (1+oldPosition)
            else writeIORef position 0
        newPosition <- readIORef position
        let gifPattern = ".gif"
            filename = (imageLst !! newPosition) in
                if filename =~ gifPattern :: Bool
                    then imageSetFromFile image filename--possibly an animation, Ignores Scaling
                    else do --Static Image, Scale away!
                        exp <- readIORef expand
                        if not exp then do
                            windowSize <- windowGetSize window
                            pix <- pixbufNewFromFileAtScale filename ((fst windowSize)-10) ((snd windowSize)-32) True
                            imageSetFromPixbuf image pix
                        else imageSetFromFile image filename
    on backButton buttonActivated $ do
        oldPosition <- readIORef position
        if (oldPosition > 0)
            then writeIORef position (oldPosition-1)
            else writeIORef position ((length imageLst)-1)
        newPosition <- readIORef position
        let gifPattern = ".gif"
            filename = (imageLst !! newPosition) in
                if filename =~ gifPattern :: Bool
                    then imageSetFromFile image filename--possibly animation, Ignores Scaling
                    else do --Static Image, Scale away!
                        exp <- readIORef expand
                        if not exp then do
                            windowSize <- windowGetSize window
                            pix <- pixbufNewFromFileAtScale filename ((fst windowSize)-10) ((snd windowSize)-32) True
                            imageSetFromPixbuf image pix
                        else imageSetFromFile image filename
    widgetShowAll window
    mainGUI

dirContents [] = do
    cwd <- getCurrentDirectory
    lst <- getDirectoryContents cwd
    let flst = filter isImage lst in
        if flst == [] then error "No images"
        else return flst
dirContents (x:xs) = do
    cwd <- getCurrentDirectory
    lst <- getDirectoryContents cwd
    let flst = filter isImage lst in
        if flst == [] then error "No images"
        else
            if elem x flst
                then return (shift x flst)
                else return flst

isImage :: String -> Bool
isImage filename = let pattern = "(.png|.jpg|.gif|.bmp|.jpeg)" in
    filename =~ pattern :: Bool

shift :: String -> [String] -> [String]
shift item lst@(x:xs) = if item == x then lst else shift item (xs++[x])

```

---

### Post by satsujinka on 2011-10-15
UPDATE 2:

Refactoring Complete:

[LIST]
[*]The toggle button that controls whether an image should be fit to the window size now calls assignScaleEvent to assign its event handler.
[*]The forward and back buttons call a generic assignMoveEvent to assign their event handler. This cuts down on the number of lines of code, but does result in a really long function invocation (since you have to include the direction to move in, what condition should trigger the position in the list to wrap around, and what the wrap around position is.)
[/LIST]

New Feature:

[LIST]
[*]Rotate the image left or right by 90 degrees. Like forward and back these two call the same function but include the direction of the rotation. Luckily the function invocation is much shorter.;)
[/LIST]
```
module Main where

import Data.Char
import Data.IORef
import Graphics.UI.Gtk
import Graphics.UI.Gtk.Gdk.PixbufAnimation
import IO
import System
import System.Directory
import Text.Regex.Posix


main = do
    initGUI
    window <- windowNew
    onDestroy window mainQuit
    scroll <- scrolledWindowNew Nothing Nothing
    scrolledWindowSetPolicy scroll PolicyAutomatic PolicyAutomatic
    vbox <- vBoxNew False 0
    hbox <- hBoxNew False 0
    set window [windowDefaultWidth := 600, windowDefaultHeight := 500,
                containerChild := vbox, containerBorderWidth := 0]
    image <- imageNew
    quit <- buttonNewFromStock stockQuit
    quitID <- on quit buttonActivated $ do mainQuit
    nextButton <- buttonNewFromStock stockGoForward
    backButton <- buttonNewFromStock stockGoBack
    rotateLeft <- buttonNewWithLabel "Rotate Left"
    rotateRight <- buttonNewWithLabel "Rotate Right"
    scaleToggle <- toggleButtonNewWithLabel "Fit to Window"
    boxPackStart hbox rotateLeft PackRepel 0
    boxPackStart hbox rotateRight PackRepel 0
    boxPackStart hbox backButton PackRepel 0
    boxPackStart hbox nextButton PackRepel 0
    boxPackEnd hbox quit PackRepel 0
    boxPackEnd hbox scaleToggle PackRepel 0
    boxPackEnd vbox hbox PackNatural 0
    boxPackStart vbox scroll PackGrow 0
    scrolledWindowAddWithViewport scroll image
    args <- getArgs
    imageLst <- dirContents args
    imageSetFromFile image (head imageLst)
    expand <- newIORef True --Used for deciding whether an image should be fullsize
    position <- newIORef 0
    assignScaleEvent window scaleToggle image imageLst position expand 
    assignMoveEvent window nextButton image imageLst (<((length imageLst)-1)) (\ x -> x+1) 0 position expand
    assignMoveEvent window backButton image imageLst (>0) (\ x -> x-1) ((length imageLst)-1) position expand
    assignRotationEvent rotateLeft image PixbufRotateCounterclockwise
    assignRotationEvent rotateRight image PixbufRotateClockwise
    widgetShowAll window
    mainGUI

dirContents [] = do
    cwd <- getCurrentDirectory
    lst <- getDirectoryContents cwd
    let flst = filter isImage lst in
        if flst == [] then error "No images"
        else return flst
dirContents (x:xs) = do
    cwd <- getCurrentDirectory
    lst <- getDirectoryContents cwd
    let flst = filter isImage lst in
        if flst == [] then error "No images"
        else
            if elem x flst
                then return (shift x flst)
                else return flst

isImage :: String -> Bool
isImage filename = let pattern = "(.png|.jpg|.gif|.bmp|.jpeg)" in
    filename =~ pattern :: Bool

shift :: String -> [String] -> [String]
shift item lst@(x:xs) = if item == x then lst else shift item (xs++[x])

assignScaleEvent :: Window -> ToggleButton-> Image -> [String] -> IORef Int -> IORef Bool -> IO()
assignScaleEvent window scale image imageLst position expand = do
    on scale toggled $ do
        pos <- readIORef position
        exp <- readIORef expand
        imageSetAndScale window image (imageLst !! pos) exp
        writeIORef expand (not exp)
    return ()

assignMoveEvent :: Window -> Button -> Image ->
                   [String] -> (Int -> Bool) -> (Int -> Int) -> Int ->
                   IORef Int -> IORef Bool -> IO ()
assignMoveEvent window button image imageLst wrapCondition move wrapToLocation position expand = do
    on button buttonActivated $ do
        oldPosition <- readIORef position
        if (wrapCondition oldPosition)
            then writeIORef position (move oldPosition)
            else writeIORef position wrapToLocation
        newPosition <- readIORef position
        exp <- readIORef expand
        imageSetAndScale window image (imageLst !! newPosition) (not exp)
    return ()

assignRotationEvent :: Button -> Image -> PixbufRotation -> IO ()
assignRotationEvent button image direction = do
    on button buttonActivated $ do
        imageType <- get image imageStorageType
        if imageType == ImagePixbuf
            then do
                pix <- imageGetPixbuf image
                pix2 <- pixbufRotateSimple pix direction
                imageSetFromPixbuf image pix2
            else putStrLn "Not applicable"
    return ()

imageSetAndScale :: Window -> Image -> String -> Bool -> IO ()
imageSetAndScale window image filename expand = do
    pixAnim <- pixbufAnimationNewFromFile filename
    static <- pixbufAnimationIsStaticImage pixAnim
    if static
        then if expand
            then do
                windowSize <- windowGetSize window
                pix <- pixbufNewFromFileAtScale filename ((fst windowSize)-10) ((snd windowSize)-32) True
                imageSetFromPixbuf image pix
            else imageSetFromFile image filename
        else imageSetFromFile image filename
    return ()

```

---

### Post by nvteighen on 2011-10-15
I've managed to install the proper dependencies from the Debian testing repos, so it's fine. I will get into the new code and enjoy it :) tomorrow.

---

### Post by satsujinka on 2011-10-16
After experimenting a bit, you need glade 3.8 to generate glade files that gtk2hs can use. I'll be switching to glade so the next code drop will be a few lines shorter. Plus there's a bug with the rotate code in that in doesn't respect fit to window. So those two things will be fixed, also a few graphical rearrangements will be done and a preference dialog will be added (which will control how far to rotate pictures.)

EDIT: By the way, I'll be uploading various Haskell related programs to a google project, the link is in my signature.

---

### Post by satsujinka on 2011-10-17
UPDATE 3:
New Feature:

[LIST]
[*]Uses glade for the interface
[*]Fullscreen mode
[*]An empty preferences dialog (rotation amount is not as easily changed as I had hoped.)
[/LIST]
Bugs Fixed:

[LIST]
[*]Rotation now respects fit to window.
[/LIST]
Known Bugs (unintentional features :wink: ):

[LIST]
[*]Fullscreen doesn't change image size (not an issue with actual size mode, but if you're using fit to window you'll have to change out and back.)
[*]I can't reproduce it but events can sometimes take effect prior to another event finishing, which leads to images that won't change size. Restarting the program fixes it though.
[/LIST]
```
module Main where

import Control.Monad.IO.Class
import Data.Char
import Data.IORef
import Graphics.UI.Gtk
import Graphics.UI.Gtk.Glade
import Graphics.UI.Gtk.Gdk.EventM
import Graphics.UI.Gtk.Gdk.PixbufAnimation
import IO
import System
import System.Directory
import Text.Regex.Posix


main = do
  initGUI
  Just xml    <- xmlNew "Layout.glade"
  window      <- xmlGetWidget xml castToWindow    "window1"             --begin window1 widgets
  hbox        <- xmlGetWidget xml castToHBox      "hbox1"
  statusbar   <- xmlGetWidget xml castToStatusbar      "statusbar1"
  image       <- xmlGetWidget xml castToImage     "image1"
  viewport    <- xmlGetWidget xml castToViewport  "viewport1"           --needed to change background on image
  back        <- xmlGetWidget xml castToButton    "button1"
  next        <- xmlGetWidget xml castToButton    "button2"
  rotateLeft  <- xmlGetWidget xml castToButton    "button3"
  rotateRight <- xmlGetWidget xml castToButton    "button4"
  fitToWindow <- xmlGetWidget xml castToButton    "button5"
  fullScreen  <- xmlGetWidget xml castToButton    "button6"
  settings    <- xmlGetWidget xml castToButton    "button7"
  quit        <- xmlGetWidget xml castToButton    "button8"
  preferences <- xmlGetWidget xml castToWindow    "window2"             --begin window2 widgets
  apply       <- xmlGetWidget xml castToButton    "button9"
  noApply     <- xmlGetWidget xml castToButton    "button10"
  args        <- getArgs
  imageLst    <- dirContents args
  fullscreen  <- newIORef False
  position    <- newIORef 0
  expand      <- newIORef True                                          --possibly read in at runtime
  imageSetAndScale image (imageLst !! 0) False
  on window objectDestroy $ do mainQuit
  on window keyPressEvent $ tryEvent $ do
    "Escape" <- eventKeyName
    liftIO $ do
      fs <- readIORef fullscreen
      if fs then do
        widgetShowAll window
        windowUnfullscreen window
      else putStrLn ""
  on back buttonActivated $ do move image imageLst (-1) position expand
  on next buttonActivated $ do move image imageLst 1 position expand
  on rotateLeft buttonActivated $ do rotate image expand PixbufRotateCounterclockwise
  on rotateRight buttonActivated $ do rotate image expand PixbufRotateClockwise
  on fitToWindow buttonActivated $ do
    fitImage image imageLst position expand
    exp <- readIORef expand
    if exp then set fitToWindow [buttonLabel := "Fit to Window"]
    else set fitToWindow [buttonLabel := "Actual Size"]
  on fullScreen buttonActivated $ do
    writeIORef fullscreen True
    windowFullscreen window
  on settings buttonActivated $ do widgetShowAll preferences
  on quit buttonActivated $ do mainQuit
  on apply buttonActivated $ do widgetHide preferences
  on noApply buttonActivated $ do widgetHide preferences
  widgetShowAll window
  mainGUI

dirContents [] = do
  cwd <- getCurrentDirectory
  lst <- getDirectoryContents cwd
  let flst = filter isImage lst in
    if flst == [] then error "No images"
    else return flst
dirContents (x:xs) = do
  cwd <- getCurrentDirectory
  lst <- getDirectoryContents cwd
  let flst = filter isImage lst in
    if flst == [] then error "No images"
    else
      if elem x flst
        then return (shift x flst)
        else return flst

isImage :: String -> Bool
isImage filename = let pattern = "(.png|.jpg|.gif|.bmp|.jpeg)" in
  filename =~ pattern :: Bool

shift :: String -> [String] -> [String]
shift item lst@(x:xs) = if item == x then lst else shift item (xs++[x])

fitImage :: Image -> [String] -> IORef Int -> IORef Bool -> IO()
fitImage image imageLst position expand = do
  pos <- readIORef position
  exp <- readIORef expand
  imageSetAndScale image (imageLst !! pos) exp
  writeIORef expand (not exp)
  return ()

move :: Image -> [String] -> Int -> IORef Int -> IORef Bool -> IO ()
move image imageLst direction position expand = do
  old <- readIORef position
  if direction == 1
    then if old >= ((length imageLst) - 1)
      then writeIORef position 0
      else writeIORef position (old + 1)
    else if old <= 0
      then writeIORef position ((length imageLst) - 1)
      else writeIORef position (old - 1)
  new <- readIORef position
  exp <- readIORef expand
  imageSetAndScale image (imageLst !! new) (not exp)
  return ()

rotate :: Image -> IORef Bool -> PixbufRotation -> IO ()
rotate image expand direction = do
  imageType <- get image imageStorageType
  if imageType == ImagePixbuf
    then do
      exp <- readIORef expand
      if not exp
        then do
          pix <- imageGetPixbuf image
          pix2 <- pixbufRotateSimple pix direction
          pixbufSave pix2 "4590temporary39403image39405path39403.png" "png" []  --tmpfile is the proper way to do this, but this is easier.
          availableSpace <- widgetGetSize image                         --returns a tuple with (widgetWidth, widgetHeight)
          pix3 <- pixbufNewFromFileAtScale "4590temporary39403image39405path39403.png" (fst availableSpace) (snd availableSpace) True
          imageSetFromPixbuf image pix3
          removeFile "4590temporary39403image39405path39403.png"
        else do
          pix <- imageGetPixbuf image
          pix2 <- pixbufRotateSimple pix direction
          imageSetFromPixbuf image pix2
    else putStrLn "Not applicable"
  return ()

imageSetAndScale :: Image -> String -> Bool -> IO ()
imageSetAndScale image filename expand = do
  pixAnim <- pixbufAnimationNewFromFile filename
  static <- pixbufAnimationIsStaticImage pixAnim
  if static
    then if expand
      then do
        availableSpace <- widgetGetSize image                           --returns a tuple with (widgetWidth, widgetHeight)
        pix <- pixbufNewFromFileAtScale filename (fst availableSpace) (snd availableSpace) True
        imageSetFromPixbuf image pix
      else imageSetFromFile image filename
    else imageSetFromFile image filename
  return ()

```

---

