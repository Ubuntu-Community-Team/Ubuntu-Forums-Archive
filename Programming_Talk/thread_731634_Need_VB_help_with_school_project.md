---
title: "Need VB help with school project"
date: 2008-03-22
forum: Programming Talk
---

### Post by Zigon on 2008-03-22
Were making an amazing tic tac toe game which well be graded. I've got everything down except the computer A.I and the looks. I'm trying to have the button change it's picture appearance when it's clicked. So far this is what I have:
```
intRow = (Index \ 3) + 1
intCol = (Index) Mod 3 + 1
If strBoard(intRow, intCol) = "" Then
    If intCounter Mod 2 = 0 Then
        strBoard(intRow, intCol) = "O"
        cmdplay(Index).Caption = "O"
        cmdplay(Index).Enabled = False
        strPlayerTwo = "Player 1"
        lblTurn.Caption = strPlayerTwo
    ElseIf intCounter Mod 2 = 1 Then
       strBoard(intRow, intCol) = "X"
        cmdplay(Index).Picture = LoadPicture(App.Path & "\X.bmp")
        strPlayerOne = "Player 1"
        cmdplay(Index).Enabled = False
        strPlayerOne = "Player 2"
        lblTurn.Caption = strPlayerOne
        
    End If
End If
```
What happens is when I click the button, the button goes back to gray but I can still a few white lines of the top part of the x, so I know it's being displayed still. At the buttem of the button it displays the "X". App.Path is leading to he right directory and as far as I know there aren't any typos. I'm sure theres a small mistake here but I can't wrap my head around it. I was going to google the rest but if anyone here knows. How can I make the button shake when I click on it? And can I use animated gifs?

EDIT: I found out the reason the picture is going all gray after it's being clicked is because the button becomes disabled. How can I have to so when a button is disabled the appearance stays the same?

---

### Post by LaRoza on 2008-03-22
> **Zigon said:**
> Were making an amazing tic tac toe game which well be graded. I've got everything down except the computer A.I and the looks. I'm trying to have the button change it's picture appearance when it's clicked. So far this is what I have:

I was going to google the rest but if anyone here knows


[list]
[*]See the sticky on how to get your homework done.
[*]You are too lazy to look for the answer? Why should others take the time to help then?
[/list]

---

### Post by Zigon on 2008-03-22
I have been looking for the answer, all I can find is stuff about disabling text boxes. I'm not asking to do my project.

---

### Post by The Cog on 2008-03-24
I've never looked at VB before, but I suspect this might be your problem:
```
cmdplay(Index).Picture = LoadPicture(App.Path & "\X.bmp")
```
In most languages, backslash has special meaning, so that for instance \n means a newline character, and for a backslash you have to use \\. So try this:
```
cmdplay(Index).Picture = LoadPicture(App.Path & "\\X.bmp")
```

---

### Post by Kadrus on 2008-03-24
I don't think you'll find a lot of Visual Basic programmers in here...besides no one will help when it's related to homework  :p ...which is a good thing,,.because you should do things on your own..
Here are some links that might help you..
[http://www.scratchprojects.com/2006/02/sample_article_tic_tac_toe_p01.php](http://www.scratchprojects.com/2006/02/sample_article_tic_tac_toe_p01.php)
[http://visualbasic.about.com/od/usingvbnet/l/aa093002a.htm](http://visualbasic.about.com/od/usingvbnet/l/aa093002a.htm)
Google is your friend..search!

---

### Post by Cappy on 2008-03-24
So, the problem is you are disabling the button? Don't disable the button with .Disable then.
Instead, check to see if the .Picture is set. If it is set to X.bmp or O.bmp or whatever then you know it has already been used.

There are a lot of different ways you could check to see if a piece is set without disabling it.

---

