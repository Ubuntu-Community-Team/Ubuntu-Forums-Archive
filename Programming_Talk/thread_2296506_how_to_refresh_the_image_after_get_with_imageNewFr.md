---
title: "how to refresh the image after get with imageNewFromFile"
date: 2015-09-26
forum: Programming Talk
---

### Post by zerop2 on 2015-09-26
if image file is updated, 
how to refresh the image in hbox after get with imageNewFromFile


```

import Graphics.Rendering.Chart.Easy
import Graphics.Rendering.Chart.Backend.Cairo
import Graphics.UI.Gtk
--import Graphics.UI.Gtk.Layout.BackgroundContainer
--import Graphics.UI.Gtk.Board.BoardLink
import Graphics.UI.Gtk.Display.Image
import Graphics.UI.Gtk.Gdk.Screen
signal :: [Double] -> [(Double,Double)]
signal xs = [ (x,(sin (x*3.14159/45) + 1) / 2 * (sin (x*3.14159/5))) | x <- xs ]


hello =
 toFile def "example1_big.png" $ do
 layout_title .= "Amplitude Modulation"
 setColors [opaque blue, opaque red]
 plot (line "am" [signal [0,(0.5)..400]])
 plot (points "am points" (signal [0,7..400]))


main :: IO ()
main = do
 hello
 initGUI
 window <- windowNew
 bgBac1   <- imageNewFromFile "example1_big.png"
 bgBac2   <- imageNewFromFile "example1_big.png"
 bgBac3   <- imageNewFromFile "example1_big.png"
 bgBac4   <- imageNewFromFile "example1_big.png"
 col  <- vBoxNew False 2
 containerAdd window col
 row0  <- hBoxNew False 2
 boxPackStart col row0 PackNatural 1
 row1  <- hBoxNew False 2
 boxPackStart col row1 PackNatural 2
 boxPackStart row0 bgBac1 PackNatural 0
 boxPackStart row0 bgBac2 PackNatural 1
 boxPackStart row1 bgBac3 PackNatural 0
 boxPackStart row1 bgBac4 PackNatural 1
 Graphics.UI.Gtk.set row0 [ containerWidth := 300 ]
 Graphics.UI.Gtk.set row1 [ containerWidth := 300 ]
 Just screen <- screenGetDefault
 rootwindow <- screenGetRootWindow screen
 size <- drawableGetSize rootwindow
 widgetSetSizeRequest window (fst size) (snd size)
 widgetShowAll window
 onDestroy window mainQuit
 mainGUI

```

---

