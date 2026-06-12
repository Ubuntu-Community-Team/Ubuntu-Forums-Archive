---
title: "When trying to make a game..."
date: 2009-10-22
forum: Programming Talk
---

### Post by Dullstar on 2009-10-22
...What paths do you follow as far as tutorials go?  What kind of stuff does one have to learn how to do?  The programming language I am liking the most of the ones I ahve tried is C.

EDIT:  Pygame FTW

---

### Post by sam191 on 2009-10-22
Do you know how to program? 

Game programming is **very** complex. Believe me, I started out wanting to write games too.

As far as stuff you need to know. You should know 1) a programming language (preferably, know it well. Which means months of coding :D) 2) a graphics API like OpenGL or DirectX or SDL.. etc. and 3) you will need art, and this is a big one. I spent more drawing then I did coding. Might want to think about that. 

If you are flying solo, I would recommend Python + Pygame, then use C where you need it. But that's just my opinion. 

Check this place out: [www.gamedev.net]("http://www.gamedev.net")

This should help you get on your feet.

---

### Post by Dullstar on 2009-10-22
I did try Python, but I admit it - I like C a whole lot better for some reason.
I've already been told it is complicated, but I did once ask a question about how to write levels, and the recommendation I got was to write a level editor.  Apparently, it's not supposedly too difficult to write for your own projects, but I don't know, because I haven't gotten that far yet! =D

---

### Post by Can+~ on 2009-10-22
> **Dullstar said:**
> I did try Python, but I admit it - I like C a whole lot better for some reason.
I've already been told it is complicated, but I did once ask a question about how to write levels, and the recommendation I got was to write a level editor.  Apparently, it's not supposedly too difficult to write for your own projects, but I don't know, because I haven't gotten that far yet! =D

A level editor with an interface? Like opening a GTK+ window with squares and the like?

Well, the basic concept of an editor is quite easy, basically, most 2d grid based games are just that, a big array which holds a different number/name for each cell, representing a certain tile/property.

The hard part would be having the interface. Interfaces are not something trivial with C.

---

### Post by sam191 on 2009-10-22
> **Dullstar said:**
> I did try Python, but I admit it - I like C a whole lot better for some reason.
I've already been told it is complicated, but I did once ask a question about how to write levels, and the recommendation I got was to write a level editor.  Apparently, it's not supposedly too difficult to write for your own projects, but I don't know, because I haven't gotten that far yet! =D

That's interesting, how long have you been coding and what's the biggest project you've done if you don't mind me asking? 

I too started to like C better than Python when I first started out, but now I won't touch C unless I have to. Also, I don't know if you've written any games so far, but Pong wouldn't be a bad place to start. Level editors means you will have levels, and if you have levels then the game will be getting pretty complicated, especially for a "first game". The reason I like Pygame is because I was able to download whole games and see how they were written, then tinker with them etc until I could write my own.

---

### Post by mike_g on 2009-10-23
One of the largest apps I ever wrote was a map editor. That was a long time ago and I kept adding features and bugs until it became a bit of a mess. 

Heres some code for a simple map editor I made for a raycasting engine I wrote. It only draws a set of tiles on a fixed size grid with no placeable objects. But it keeps things nice and simple. The code is in Blitz Basic, but the basic approach would work in SDL quite easily.
```
AppTitle "Level Editor"
Graphics 800, 600, 32, 2
SetBuffer BackBuffer()

Const TILE_TYPES=12
Global x_cells=75
Global y_cells=75

Dim tile_col(TILE_TYPES)
Dim tile_name$(TILE_TYPES)
LoadTileset()


Dim map(x_cells, y_cells)
InitMap()
Global screen = CreateImage(800, 600)
InitScreen()

Global selected

wait=CreateTimer(60)
While Not KeyHit(1)
    Cls 
    DrawImage screen, 0, 0
    MouseInput()
    Flip 
    WaitTimer(wait)
Wend

;----------------------------------------------------------------------------------------------;
;******************************* INITAILIZATION FUNCTIONS *************************************;
;----------------------------------------------------------------------------------------------;
Function InitScreen()
    SetBuffer ImageBuffer(screen)
    LockBuffer
    For y=0 To 599
        For x=0 To 599
            If map(x/8, y/8) >=0
                WritePixelFast(x, y, tile_col(map(x/8, y/8)))
            EndIf 
        Next
    Next
    UnlockBuffer
    DrawGridLines()
    UpdateSidebar()
End Function

Function InitMap()
    For y=0 To y_cells-1
        For x=0 To x_cells-1
            map(x, y)=-1
        Next
    Next
    
    
    For y = 0 To y_cells-1
        map(0, y)=0
        map(x_cells-1, y)=0
    Next
    For x = 0 To x_cells-1
        map(x, 0)=0
        map(x, y_cells-1)=0
    Next
End Function

Function LoadTileset()
    tile_col(0)=$225511:    tile_name$(0)="Hedge"
    tile_col(1)=$555555:    tile_name$(1)="Wall"
    tile_col(2)=$888888:    tile_name$(2)="Pillar"
    tile_col(3)=$555522:    tile_name$(3)="Wood"
    tile_col(4)=$333366:    tile_name$(4)="Windows"
    tile_col(5)=$666655:    tile_name$(5)="Door"
    tile_col(6)=$403300:    tile_name$(6)="Cliff"
    tile_col(7)=$556644:    tile_name$(7)="Overgrown"
    tile_col(8)=$555566:    tile_name$(8)="Stone"
    tile_col(9)=$775522:    tile_name$(9)="Decking"
    tile_col(10)=$888866:    tile_name$(10)="Door 2"
    tile_col(11)=$BBBBAA:    tile_name$(11)="House"
End Function

;----------------------------------------------------------------------------------------------;
;************************************ INPUT FUNCTIONS *****************************************;
;----------------------------------------------------------------------------------------------;
Function MouseInput()
    mx=MouseX()
    my=MouseY()
    If MouseDown(1)
        If mx < 601
            x_pos=mx/8
            y_pos=my/8
            If x_pos=0 Or x_pos=x_cells-1 Or y_pos=0 Or y_pos=y_cells-1
                If selected >= 0 ;cant delete edge walls
                    map(x_pos, y_pos)=selected    
                    UpdateTile(x_pos*8, y_pos*8)                
                EndIf 
            Else
                map(x_pos, y_pos)=selected    
                UpdateTile(x_pos*8, y_pos*8)
            EndIf 
        Else
            If my > 39 And my < 20+TILE_TYPES*40
                selected=(MouseY()-30)/40
                UpdateSidebar()
            Else If my > 8+TILE_TYPES*40 And my < 40+TILE_TYPES*40
                selected=-1
                UpdateSidebar()
            Else If my > 560 And my < 592
                If mx > 620 And mx < 684
                    SaveMap(200, 300)
                Else If mx > 720 And mx < 784
                    LoadMap(200, 300)
                EndIf 
            EndIf 
        EndIf 
    EndIf 
End Function 
;----------------------------------------------------------------------------------------------;
;************************************* DRAW FUNCTIONS *****************************************;
;----------------------------------------------------------------------------------------------;

Function UpdateTile(x_pos, y_pos)
    If selected=-1
        col=0
    Else
        col=tile_col(selected)
    EndIf      
    SetBuffer ImageBuffer(screen)
    LockBuffer 
    For y=y_pos+1 To y_pos+7
        For x=x_pos+1 To x_pos+7
            WritePixelFast(x, y, col)
        Next
    Next
    UnlockBuffer
    SetBuffer BackBuffer()
End Function

Function DrawGridLines()
    Color 40, 40, 40
    For i=0 To 600 Step 8
        Line i, 0, i, 600
        Line 0, i, 600, i
    Next
End Function 

Function UpdateSidebar()
    SetBuffer ImageBuffer(screen)
    ;CLEAR SIDEBAR
    Color 10, 10, 20
    Rect 601, 0, 200, 600, 1

    Color 20, 20, 40
    Rect 601, 1, 100, 20, 1 
    Color 100, 100, 100
    Text 610, 4, "PLACEABLES"
    Text 730, 4, "TILES"
        
    ;TILE TYPES     
    For i=0 To TILE_TYPES-1
        If i=selected 
            Color 150, 0, 0
            Rect 632, 30+(i*40), 146, 36, 0
        EndIf 
        Color 150, 150, 150
        Text 640, 40+(i*40), tile_name$(i)     
        LockBuffer
        y_pos = 32+(i*40)
        For y=y_pos To y_pos+31
            For x=740 To 771
                WritePixelFast(x, y, tile_col(i))
            Next
        Next    
        UnlockBuffer
    Next
    
    ;DELETE BUTTON
    Color 150, 150, 150
    Text 640, 40+(i*40), "Delete"
    Color 150, 0, 0
    Rect 740, 30+(i*40), 32, 32, 1
    If selected=-1
        Rect 632, 28+(i*40), 146, 36, 0    
    EndIf 
    Color 150, 150, 150
    Rect 740, 30+(i*40), 32, 32, 0
    Line 740, 30+(i*40), 771, 61+(i*40)
    Line 771, 30+(i*40), 740, 61+(i*40) 

    
    ;SAVE AND LOAD BUTTONS
    Color 60, 30, 30
    Rect 620, 560, 64, 32, 1
    Rect 720, 560, 64, 32, 1
    Color 100, 100, 100
    Rect 620, 560, 64, 32, 0
    Rect 720, 560, 64, 32, 0    
    Text 634, 570, "SAVE"
    Text 734, 570, "LOAD"
    SetBuffer BackBuffer()
End Function

Function FileRect(x, y)
    Color 10, 10, 30
    Rect x, y, 300, 30, 1
    Color 50, 50, 50
    Rect x, y, 300, 30, 0
End Function 

;----------------------------------------------------------------------------------------------;
;******************************** SAVE AND LOAD FUNCTIONS *************************************;
;----------------------------------------------------------------------------------------------;

Function SaveMap(x, y)
    FileRect(x, y)
    Locate x+10, y+10
    saveas$=Input("SAVE AS:")    
    file=WriteFile(saveas$+".lvl")
    WriteByte(file, x_cells)
    WriteByte(file, y_cells)
    For y=0 To y_cells-1
        For x=0 To x_cells-1
            WriteByte(file, map(x, y)+1)
        Next
    Next
    CloseFile(file)
End Function

Function LoadMap(x, y)
    FileRect(x, y)
    Locate x+10, y+10
    load$=Input("LOAD:")    
    file=OpenFile(load$+".lvl")
    If file = 0
        FileRect(x, y)
        Text x+10, y+10, "FILE NOT FOUND"
        WaitKey    
        Return False
    EndIf  
    x_cells=ReadByte(file)
    y_cells=ReadByte(file)
    For y=0 To y_cells-1
        For x=0 To x_cells-1
            selected=ReadByte(file)-1
            map(x, y)=selected
            UpdateTile(x*8, y*8)
        Next
    Next
    selected=0
    CloseFile(file)
End Function 
```

Also, I don't see any need to use Gtk or the like if all you need are a few buttons and maybe a scrollbar or two. That stuff is not too difficult to code from scratch.

---

### Post by Dullstar on 2009-10-23
I'm going to make it have JUST enough features to function - Save, Load, Delete, Connect (for connecting multiple maps together), and edit maps.

---

### Post by Simian Man on 2009-10-23
There are basically three approaches that I can think of when making a level editor:

[LIST=1]
[*]You can use a traditional GUI toolkit such as Gtk, QT, wxWidgets etc. for the window and interface elements and then draw your game elements to a generic "canvas" element that most toolkits provide with your graphics API of choice.

[*]You can use your graphics API of choice to open a window and draw your game elements and use a special game GUI library like CEGUI, Agar or ParaGUI to draw your interface controls via the graphics API.

[*]You can use your graphics API of choice to open a window and draw your game elements and UI controls manually.
[/LIST]

The best option to choose depends on several things.

First off if you plan on distributing the editor to your users for modding purposes, then choosing the first option is attractive since the interface will look more natural and be easier to use.  Also the more complicated your needs are the more UI elements you will need and the more work will be saved by going with an established library (the first two options).

However, if you just need an editor to use yourself, and just want a couple buttons and a text box, going with the third option will be the quickest and simplest.  Also most games will require some UI elements, so going with options 2 or 3 will mean you can reuse the work from the editor in your actual game.

For the editor for a game I wrote, and went with option 3.  It looked like crap but only I ever saw it.  It also worked wonderfully and only took a few hundred lines of code.

BTW I'd suggest using SDL as your library.  It is one of the best designed APIs I have ever used, and is well supported on Linux.  I'd also suggest using Python with PyGame (which is just a Python binding to SDL).  If you stick with C, plan on spending a long time learning mundane details as opposed to programming your game.

---

### Post by Dullstar on 2009-10-23
You know, since my upgrade to the 9.10 beta, I've been having to reinstall packages anyway, so I might try Python again.

Anyway, the third option will be good enough for me, if it's going to be simple.

---

### Post by Dullstar on 2010-02-07
Pygame's been working great, but the tutorials I found just kinda dump you after a few basic things.  Can anyone tell me somewhere I can find a tutorial to give me at least some idea of how to make a platformer?  I know it's complicated, but I'd like to give it a shot.

---

### Post by Dullstar on 2010-02-07
> **mike_g said:**
> One of the largest apps I ever wrote was a map editor. That was a long time ago and I kept adding features and bugs until it became a bit of a mess. 

Heres some code for a simple map editor I made for a raycasting engine I wrote. It only draws a set of tiles on a fixed size grid with no placeable objects. But it keeps things nice and simple. The code is in Blitz Basic, but the basic approach would work in SDL quite easily.
```
AppTitle "Level Editor"
Graphics 800, 600, 32, 2
SetBuffer BackBuffer()

Const TILE_TYPES=12
Global x_cells=75
Global y_cells=75

Dim tile_col(TILE_TYPES)
Dim tile_name$(TILE_TYPES)
LoadTileset()


Dim map(x_cells, y_cells)
InitMap()
Global screen = CreateImage(800, 600)
InitScreen()

Global selected

wait=CreateTimer(60)
While Not KeyHit(1)
    Cls 
    DrawImage screen, 0, 0
    MouseInput()
    Flip 
    WaitTimer(wait)
Wend

;----------------------------------------------------------------------------------------------;
;******************************* INITAILIZATION FUNCTIONS *************************************;
;----------------------------------------------------------------------------------------------;
Function InitScreen()
    SetBuffer ImageBuffer(screen)
    LockBuffer
    For y=0 To 599
        For x=0 To 599
            If map(x/8, y/8) >=0
                WritePixelFast(x, y, tile_col(map(x/8, y/8)))
            EndIf 
        Next
    Next
    UnlockBuffer
    DrawGridLines()
    UpdateSidebar()
End Function

Function InitMap()
    For y=0 To y_cells-1
        For x=0 To x_cells-1
            map(x, y)=-1
        Next
    Next
    
    
    For y = 0 To y_cells-1
        map(0, y)=0
        map(x_cells-1, y)=0
    Next
    For x = 0 To x_cells-1
        map(x, 0)=0
        map(x, y_cells-1)=0
    Next
End Function

Function LoadTileset()
    tile_col(0)=$225511:    tile_name$(0)="Hedge"
    tile_col(1)=$555555:    tile_name$(1)="Wall"
    tile_col(2)=$888888:    tile_name$(2)="Pillar"
    tile_col(3)=$555522:    tile_name$(3)="Wood"
    tile_col(4)=$333366:    tile_name$(4)="Windows"
    tile_col(5)=$666655:    tile_name$(5)="Door"
    tile_col(6)=$403300:    tile_name$(6)="Cliff"
    tile_col(7)=$556644:    tile_name$(7)="Overgrown"
    tile_col(8)=$555566:    tile_name$(8)="Stone"
    tile_col(9)=$775522:    tile_name$(9)="Decking"
    tile_col(10)=$888866:    tile_name$(10)="Door 2"
    tile_col(11)=$BBBBAA:    tile_name$(11)="House"
End Function

;----------------------------------------------------------------------------------------------;
;************************************ INPUT FUNCTIONS *****************************************;
;----------------------------------------------------------------------------------------------;
Function MouseInput()
    mx=MouseX()
    my=MouseY()
    If MouseDown(1)
        If mx < 601
            x_pos=mx/8
            y_pos=my/8
            If x_pos=0 Or x_pos=x_cells-1 Or y_pos=0 Or y_pos=y_cells-1
                If selected >= 0 ;cant delete edge walls
                    map(x_pos, y_pos)=selected    
                    UpdateTile(x_pos*8, y_pos*8)                
                EndIf 
            Else
                map(x_pos, y_pos)=selected    
                UpdateTile(x_pos*8, y_pos*8)
            EndIf 
        Else
            If my > 39 And my < 20+TILE_TYPES*40
                selected=(MouseY()-30)/40
                UpdateSidebar()
            Else If my > 8+TILE_TYPES*40 And my < 40+TILE_TYPES*40
                selected=-1
                UpdateSidebar()
            Else If my > 560 And my < 592
                If mx > 620 And mx < 684
                    SaveMap(200, 300)
                Else If mx > 720 And mx < 784
                    LoadMap(200, 300)
                EndIf 
            EndIf 
        EndIf 
    EndIf 
End Function 
;----------------------------------------------------------------------------------------------;
;************************************* DRAW FUNCTIONS *****************************************;
;----------------------------------------------------------------------------------------------;

Function UpdateTile(x_pos, y_pos)
    If selected=-1
        col=0
    Else
        col=tile_col(selected)
    EndIf      
    SetBuffer ImageBuffer(screen)
    LockBuffer 
    For y=y_pos+1 To y_pos+7
        For x=x_pos+1 To x_pos+7
            WritePixelFast(x, y, col)
        Next
    Next
    UnlockBuffer
    SetBuffer BackBuffer()
End Function

Function DrawGridLines()
    Color 40, 40, 40
    For i=0 To 600 Step 8
        Line i, 0, i, 600
        Line 0, i, 600, i
    Next
End Function 

Function UpdateSidebar()
    SetBuffer ImageBuffer(screen)
    ;CLEAR SIDEBAR
    Color 10, 10, 20
    Rect 601, 0, 200, 600, 1

    Color 20, 20, 40
    Rect 601, 1, 100, 20, 1 
    Color 100, 100, 100
    Text 610, 4, "PLACEABLES"
    Text 730, 4, "TILES"
        
    ;TILE TYPES     
    For i=0 To TILE_TYPES-1
        If i=selected 
            Color 150, 0, 0
            Rect 632, 30+(i*40), 146, 36, 0
        EndIf 
        Color 150, 150, 150
        Text 640, 40+(i*40), tile_name$(i)     
        LockBuffer
        y_pos = 32+(i*40)
        For y=y_pos To y_pos+31
            For x=740 To 771
                WritePixelFast(x, y, tile_col(i))
            Next
        Next    
        UnlockBuffer
    Next
    
    ;DELETE BUTTON
    Color 150, 150, 150
    Text 640, 40+(i*40), "Delete"
    Color 150, 0, 0
    Rect 740, 30+(i*40), 32, 32, 1
    If selected=-1
        Rect 632, 28+(i*40), 146, 36, 0    
    EndIf 
    Color 150, 150, 150
    Rect 740, 30+(i*40), 32, 32, 0
    Line 740, 30+(i*40), 771, 61+(i*40)
    Line 771, 30+(i*40), 740, 61+(i*40) 

    
    ;SAVE AND LOAD BUTTONS
    Color 60, 30, 30
    Rect 620, 560, 64, 32, 1
    Rect 720, 560, 64, 32, 1
    Color 100, 100, 100
    Rect 620, 560, 64, 32, 0
    Rect 720, 560, 64, 32, 0    
    Text 634, 570, "SAVE"
    Text 734, 570, "LOAD"
    SetBuffer BackBuffer()
End Function

Function FileRect(x, y)
    Color 10, 10, 30
    Rect x, y, 300, 30, 1
    Color 50, 50, 50
    Rect x, y, 300, 30, 0
End Function 

;----------------------------------------------------------------------------------------------;
;******************************** SAVE AND LOAD FUNCTIONS *************************************;
;----------------------------------------------------------------------------------------------;

Function SaveMap(x, y)
    FileRect(x, y)
    Locate x+10, y+10
    saveas$=Input("SAVE AS:")    
    file=WriteFile(saveas$+".lvl")
    WriteByte(file, x_cells)
    WriteByte(file, y_cells)
    For y=0 To y_cells-1
        For x=0 To x_cells-1
            WriteByte(file, map(x, y)+1)
        Next
    Next
    CloseFile(file)
End Function

Function LoadMap(x, y)
    FileRect(x, y)
    Locate x+10, y+10
    load$=Input("LOAD:")    
    file=OpenFile(load$+".lvl")
    If file = 0
        FileRect(x, y)
        Text x+10, y+10, "FILE NOT FOUND"
        WaitKey    
        Return False
    EndIf  
    x_cells=ReadByte(file)
    y_cells=ReadByte(file)
    For y=0 To y_cells-1
        For x=0 To x_cells-1
            selected=ReadByte(file)-1
            map(x, y)=selected
            UpdateTile(x*8, y*8)
        Next
    Next
    selected=0
    CloseFile(file)
End Function 
```Also, I don't see any need to use Gtk or the like if all you need are a few buttons and maybe a scrollbar or two. That stuff is not too difficult to code from scratch.

I'm not even familiar with that language, but it looks like I might be able to, to a point, get it to work in Pygame, if I looked at the code and guessed what it would logically do.

---

