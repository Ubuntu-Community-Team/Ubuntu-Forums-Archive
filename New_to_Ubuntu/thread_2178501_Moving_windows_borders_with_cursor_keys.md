---
title: "Moving windows borders with cursor keys"
date: 2013-10-03
forum: New to Ubuntu
---

### Post by Kevin McCready on 2013-10-03
Is there a way to move the borders of a window on the screen without using the mouse?

---

### Post by slickymaster on 2013-10-03
In a non-maximized window do the following:

[LIST=1]
[*]Press the Alt+Space keys simultaneously
[*]A menu should open
[*]Navigate to the _M_ove option using your cursor keys (arrow keys) or alternatively press the letter 'm'
[*]The mouse pointer will appear in the middle of the window
[*]Use the cursor keys to move the window up, down, right, or left
[*]Once the window is positioned, press “Enter”.
[/LIST]

---

### Post by slickymaster on 2013-10-03
You can use the same method also to change the window size, move to another workplace, etc.

---

### Post by heir4c on 2013-10-03
[http://askubuntu.com/questions/18243/moving-windows-from-the-keyboard](http://askubuntu.com/questions/18243/moving-windows-from-the-keyboard)

---

### Post by Kevin McCready on 2013-10-03
Thanks Guys, but no luck.
I could move the window around the screen, but not adjust any of the four borders independently. Also on my laptop Presario-CQ57-Notebook I don't know how to do 
Ctrl+Alt+Num 1 = moves the window to the bottom left corner
    Ctrl+Alt+Num 2 = moves the window to the bottom half of the screen
    Ctrl+Alt+Num 3 = moves the window to the bottom right corner
    Ctrl+Alt+Num 4 = moves the window to the left half of the screen
    Ctrl+Alt+Num 5 = maximizes the window
    Ctrl+Alt+Num 6 = moves the window to the right half of the screen
    Ctrl+Alt+Num 7 = moves the window to the right left corner
    Ctrl+Alt+Num 8 = moves the window to the top half of the screen
    Ctrl+Alt+Num 9 = moves the window to the right right coner

If I press ctr-alt-number, nothing happens.

---

### Post by vasa1 on 2013-10-03
> **heir4c said:**
> [http://askubuntu.com/questions/18243/moving-windows-from-the-keyboard](http://askubuntu.com/questions/18243/moving-windows-from-the-keyboard)I think slickymaster's answer is relevant because OP specified Lubuntu. The link you provided relates to Ubuntu which doesn't use Openbox as the window manager.

---

### Post by vasa1 on 2013-10-03
Okay, so you want to resize windows and move them or just resize them?
If you want to resize them, you may need to look at ~/.config/openbox/lubuntu-rc.xml. There, you can set up keyboard combinations of your choice: [http://pclosmag.com/html/Issues/201107/page08.html](http://pclosmag.com/html/Issues/201107/page08.html) is a good starting point and of course you can look at the Openbox pages starting at [http://openbox.org/wiki/Help:Contents#Configuration](http://openbox.org/wiki/Help:Contents#Configuration). I'm mentioning Openbox because that is what makes possible what you want to do.

Check out [http://openbox.org/wiki/Help:Actions](http://openbox.org/wiki/Help:Actions), especially section 5.22 and the following ones.

---

### Post by Kevin McCready on 2013-10-03
I put
<keybind key="W-F10">
  <action name="MoveResizeTo">
    <!-- put the window in the bottom right corner -->
    <x>-0</x>
    <y>-0</y>
  </action>
</keybind>

into
~/.config/openbox/lubuntu-rc.xml

and when I did SuperUser Key + F10

it acted like alt-f

---

### Post by vasa1 on 2013-10-04
Did you run "openbox --reconfigure"?

[https://help.ubuntu.com/community/Lubuntu/Windows#Reposition_and_Resize_Windows_Without_Using_a_Mouse](https://help.ubuntu.com/community/Lubuntu/Windows#Reposition_and_Resize_Windows_Without_Using_a_Mouse)

Your code works as you'd expect for me.

Did you make any changes to lubuntu-rc.xml previously?

---

### Post by Kevin McCready on 2013-10-04
I don't run reconfigue, I just turn the machine off and then on. I do this for any changes I make in the lubuntu-rc.xml  file, which I've been doing for a long time now.

---

### Post by vasa1 on 2013-10-04
> **Kevin McCready said:**
> I don't run reconfigue, I just turn the machine off and then on. I do this for any changes I make in the lubuntu-rc.xml  file, which I've been doing for a long time now.
Without more information, it's going to be difficult to understand why your code isn't working.

And> it acted like alt-f  is really odd. What does **alt-f** do for you? Have you assigned **alt-f** to something in lubuntu-rc.xml?

I wouldn't  assign **alt-f** to anything in lubuntu-rc.xml because that combination is used by most GUI-programs already.

Maybe you could upload your lubuntu-rc.xml to pastebin so that people can look it over.

Whether you've been doing it for a long time now or not, turning the machine off and on isn't necessary if you just want to make changes to lubuntu-rc.xml effective. Plus, running **openbox --reconfigure** has diagnostic value and I would recommend you do so each time immediately you alter lubuntu-rc.xml so that you can revert to a backup easily.

---

