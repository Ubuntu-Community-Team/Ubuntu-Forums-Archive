---
title: "Copy and Paste - Shortcuts"
date: 2016-10-29
forum: New to Ubuntu
---

### Post by jv10 on 2016-10-29
Hello everyone,

I just installed Ubuntu yesterday. Time to leave windows behind. So anyway I am really new and as everyone in the start I need help.

I always used CTRL+C & CTRL+V to copy and paste and I want to keep this to make it smoother to change from Windows to Linux.

I know that in the terminal you can change this by going into preferences (not recommended sence CTRL+C is killer app) that's ok i understand that.

My problem is:
In the desktop environment (Browser / File manager) I can't use the Copy paste with those short-cuts.

I have tried to make custom short-cuts but I don't really know how to do them. see attached.

Can someone help me?

What i want is to copy and paste in the browser or files or in text editor with CTRL+C & CTRL+V

---

### Post by vasa1 on 2016-10-29
Your image is too small to read clearly :(

Can you post a better, larger image?

---

### Post by jv10 on 2016-10-29
> **vasa1 said:**
> Your image is too small to read clearly :(

Can you post a better, larger image?

Sorry about that I was used to use Photoshop and now with the GIMP just takes time.

Thank you for having a look.

---

### Post by vasa1 on 2016-10-29
Instead of GIMP, you can try gnome-screenshot which should be present by default on your system. Read *man gnome-screenshot* for how to select a defined area of the screen.

The warning is quite appropriate! Shift plus any letter is commonly used to capitalize that letter.

I'm not sure it's that difficult to get used to the defaults for copy/pasting whether it's in the file manager or terminal. The sooner you embrace Linux, the better rather than trying to preserve habits from Windows :)

---

### Post by yetimon_64 on 2016-10-29
> **jv10 said:**
> ...
What i want is to copy and paste in the browser or files or in text editor with CTRL+C & CTRL+V

I am not sure why they aren't working for you but those 2, "ctrl + c" and "ctrl + v", are the standard combinations for copy and paste on linux as well when used in a browser or text editor etc.

In fact the keyboard shortcuts for cut copy and paste are the same as in windows. The only exception is when using them in the terminal, you add the shift key as well eg. "shift + ctrl + c" for copying and "shift + ctrl + v" for pasting. 

An example of usage of the combinations; if I am in a text editor I can copy a selection of text with "ctrl + c", if I then go to a terminal and insert the cursor I can paste the copied text from the text editor into the terminal using "shift + ctrl + v". If I want to go the other way I can select a section of code or text in the terminal and press "shift + ctrl + c", and then go to the text editor and paste it with "ctrl +v".

Try using them as you would have in windows but if the terminal is involved add the shift key as well to the standard key combination.

---

### Post by jv10 on 2016-10-29
> **vasa1 said:**
> Instead of GIMP, you can try gnome-screenshot which should be present by default on your system. Read *man gnome-screenshot* for how to select a defined area of the screen.

Ohhh thank you i will have a look into that

---

### Post by jv10 on 2016-10-29
@ yetimon_64 I did some digging and i found why is not working,

It seams that every time i press CTRL it acts like a SHIFT.

Do any of you know how to sort this out?

---

### Post by vasa1 on 2016-10-29
Could you post the output from```
xmodmap -pke | grep -Ei '(control|shift)'

```between code tags for people to look at?

Mine is this:
```
keycode  37 = Control_L NoSymbol Control_L
keycode  50 = Shift_L NoSymbol Shift_L
keycode  62 = Shift_R NoSymbol Shift_R
keycode  92 = ISO_Level3_Shift NoSymbol ISO_Level3_Shift
keycode 105 = Control_R NoSymbol Control_R

```on a Dell 1545 laptop

---

### Post by jv10 on 2016-10-29
[QUOTE=vasa1;13563202]Could you post the output from```
xmodmap -pke | grep -Ei '(control|shift)'

```between code tags for people to look at?


Please see attached

---

### Post by col48 on 2016-10-29
For what it is worth, mine looks exactly the same as jv10's (post #9):

```
keycode  37 = Control_L NoSymbol Control_L
keycode  50 = Shift_L NoSymbol Shift_L
keycode  62 = Shift_R NoSymbol Shift_R
keycode  92 = ISO_Level3_Shift NoSymbol ISO_Level3_Shift
keycode 105 = Control_R NoSymbol Control_R
keycode 108 = ISO_Level3_Shift Multi_key ISO_Level3_Shift Multi_key

```

(Desktop where Ctrl+c and ctrl+v work as expected)

---

### Post by jv10 on 2016-10-29
> **col48 said:**
> For what it is worth, mine looks exactly the same as jv10's (post #9):
(Desktop where Ctrl+c and ctrl+v work as expected)

At least nothing is wrong there.

Every time i hit CTRL+C it just capitalises the "c"

c -> C

---

### Post by Bucky Ball on 2016-10-29
```
 xmodmap -pke | grep -Ei '(control|shift)'
keycode  37 = Control_L NoSymbol Control_L
keycode  50 = Shift_L NoSymbol Shift_L
keycode  62 = Shift_R NoSymbol Shift_R
keycode  92 = ISO_Level3_Shift NoSymbol ISO_Level3_Shift
keycode 105 = Control_R NoSymbol Control_R
```

Ditto. All working as it should here. 

@jv10: What make and model of machine are you using? Just out of curiousity, and this is something that doesn't work in Windows so is gift from Linux to you, could you highlight some text, open a blank text editor document (Libreoffice writer or Leafpad or something) and press the scroll wheel on your mouse. Does that copy the highlighted text into the text editor? It should. Wondering if there's some connection there. :-k

---

### Post by vasa1 on 2016-10-29
I don't know what's happening :confused:

Try```
xev -event keyboard | grep -m 1 -A 2 "KeyPress event"
```A small window will open; without changing focus or clicking on that window, press the control key you say works like the shift key. There'll be some output in the terminal: paste that output here.

---

### Post by jv10 on 2016-10-29
> **Bucky Ball said:**
> 

Ditto. All working as it should here. 

@jv10: What make and model of machine are you using? Just out of curiousity, and this is something that doesn't work in Windows so is gift from Linux to you, could you highlight some text, open a blank text editor document (Libreoffice writer or Leafpad or something) and press the scroll wheel on your mouse. Does that copy the highlighted text into the text editor? It should. Wondering if there's some connection there. :-k

My computer is a MSI GE70 2PE APACHE PRO

EDITED: It does copy and paste instantly in the browser

---

### Post by jv10 on 2016-10-29
> **vasa1 said:**
> I don't know what's happening :confused:

Try```
xev -event keyboard | grep -m 1 -A 2 "KeyPress event"
```


Please see attached.

I think I was right in that one is acting like it was a Shift.

---

### Post by HermanAB on 2016-10-29
BTW, Linux supports multiple copy buffers and there is for example also highlight and middle click which is quite convenient.  

So you could use ctrl-c to put something in the primary copy buffer and use highlight middle click to copy something else, without destroying the primary copy buffer.

Note that on a Mac, the primary copy buffer can be accessed with cmd-c and cmd-v, while the secondary copy buffer can be accessed with ctrl-k and ctrl-y, though I have encountered Mac applications that assign ctrl-k or ctrl-y to something else, thus making it inconsistent.

---

### Post by yetimon_64 on 2016-10-29
What keyboard layout do you have set up in System Settings > Text input ? Sometimes if you don't have the correct layout chosen the key inputs can be affected.

---

### Post by jv10 on 2016-10-29
> **yetimon_64 said:**
> What keyboard layout do you have set up in System Settings > Text input ? Sometimes if you don't have the correct layout chosen the key inputs can be affected.

Please see attached. 
I'm using the English UK.

---

### Post by jv10 on 2016-10-29
> **HermanAB said:**
> BTW, Linux supports multiple copy buffers and there is for example also highlight and middle click which is quite convenient.  

So you could use ctrl-c to put something in one copy buffer and use highlight middle click to copy something else, without destroying the first copy buffer.

The only problem is that every time that i click "CTRL+C" it acts like "SHIFT+C"
=/

---

### Post by yetimon_64 on 2016-10-29
> **jv10 said:**
> Please see attached. 
I'm using the English UK.

Press the keyboard symbol at the bottom right of the input pane and compare the keyboard image that pops up with your actual hardware. You may possibly be better off with the English US setting, set it then press the keyboard symbol again and see if that then matches your actual hardware more accurately.

---

### Post by jv10 on 2016-10-29
> **yetimon_64 said:**
> Press the keyboard symbol at the bottom right of the input pane and compare the keyboard image that pops up with your actual hardware. You may possibly be better off with the English US setting, set it then press the keyboard symbol again and see if that then matches your actual hardware.

Almost everything lights in the  LSHIFT (left shift)

Both CTRL ( left & right)
Both ALT ( left & right)
RSHIFT (right shift)

=0

---

### Post by jv10 on 2016-10-29
If i change to the "English US"

The output is the same. =/

Does anyone ever saw this?

---

### Post by vasa1 on 2016-10-29
I had once used *xmodmap -e* to assign / reassign keys but I don't know what OP has done to reach the current state of affairs :(

I hope practitioners of Unity can help sort things out!

---

### Post by vasa1 on 2016-10-29
> **jv10 said:**
> ...
Every time i hit CTRL+C it just capitalises the "c"

c -> C

> **jv10 said:**
> ...
I think I was right in that one is acting like it was a Shift.

> **jv10 said:**
> The only problem is that every time that i click "CTRL+C" it acts like "SHIFT+C"
=/

You should be having two shift and two control keys. Do both control keys mimic the shift keys? What does each shift key do?

---

### Post by jv10 on 2016-10-29
> **vasa1 said:**
> You should be having two shift and two control keys. Do both control keys mimic the shift keys? What does each shift key do?

Yes both CTRL, both SHIFT and also both ALT

Mimic the left SHIFT

---

### Post by vasa1 on 2016-10-29
> **jv10 said:**
> Yes both CTRL, both SHIFT and also both ALT

Mimic the left SHIFTAnd you can't remember doing *anything* that may have caused this?

---

### Post by jv10 on 2016-10-29
> **vasa1 said:**
> And you can't remember doing *anything* that may have caused this?

I have tried a couple of codes before I open the post but I can't remember what codes I have entered in the Terminal. 

Is there anyway to asign keys?

---

### Post by vasa1 on 2016-10-29
You said in your first post that you installed Ubuntu yesterday. In that case, please post the entire contents of ~/.bash_history for us to look at. Maybe someone will figure what you did, *if* it was done in the terminal.

Another somewhat drastic suggestion is to rename ~/.config to something like ~/.config.bak, log out and log back in. If all keys work as they should conventionally, we'll know it is some setting located in ~/.config and take it from there. 

Otherwise, one may need to look at all the dot files in your home folder :(

---

### Post by jv10 on 2016-10-29
Ok boys i have installed the Tweak tool

and if i change the Caps lock to act as a CTRL i can than copy and past with CAPS LOCK+C and CAPS LOCK + V

don't know if this helps but it's something

---

### Post by jv10 on 2016-10-29
> **vasa1 said:**
> please post the entire contents of ~/.bash_history for us to look at. Maybe someone will figure what you did, *if* it was done in the terminal.

It's returning Permission denied. =/

---

### Post by jv10 on 2016-10-29
Did some more tests and all the keys (CTRL & ALT) both left and right are returning the same keycode = 50

can i change the keycode?

---

### Post by jv10 on 2016-10-29
> **vasa1 said:**
> You said in your first post that you installed Ubuntu yesterday. In that case, please post the entire contents of ~/.bash_history for us to look at. Maybe someone will figure what you did, *if* it was done in the terminal.

Another somewhat drastic suggestion is to rename ~/.config to something like ~/.config.bak, log out and log back in. If all keys work as they should conventionally, we'll know it is some setting located in ~/.config and take it from there. 

Otherwise, one may need to look at all the dot files in your home folder :(

So i took a drastic measure i completely formated Ubuntu and just installed it again.

Problem is still here. So was nothing that i installed or changed.

---

### Post by vasa1 on 2016-10-29
> **jv10 said:**
> So i took a drastic measure i completely formated Ubuntu and just installed it again.

Problem is still here. So was nothing that i installed or changed.

I think we'll have to take several steps back :(

Where did you get "ubuntu" from? Did you checksum the iso?

Is this now a full install on your hard disk or are you doing all this from a pen drive or dvd?

... Can you try with another keyboard?

**Can you copy/paste stuff with your touchpad/mouse?** This is important because at some time or the other you'll want to post more than a screen's worth of information and we prefer if you paste information here between [noparse]```
 and 
``` tags[/noparse] and not as images. Using code tags is really important and we'd appreciate your taking the care to do so! **Please answer this part clearly.**

Please post the output of```
echo -e "Version $(lsb_release -a)
Session: $DESKTOP_SESSION
Desktop: $XDG_CURRENT_DESKTOP
Window Manager: $(wmctrl -m | awk '/Name:/{print $2}')
Kernel info: $(uname -a)"
```

---

### Post by Bucky Ball on 2016-10-29
Please see green link in the first line of my signature at the bottom of this post if you are confused about using code tags, but yes, please use. :)

---

### Post by vasa1 on 2016-10-29
I asked the OP to post the output of
```
xmodmap -pke | grep -Ei '(control|shift)'
```
The response was:
```
keycode  37 = Control_L NoSymbol Control_L
keycode  50 = Shift_L NoSymbol Shift_L
keycode  62 = Shift_R NoSymbol Shift_R
keycode  92 = ISO_Level3_Shift NoSymbol ISO_Level3_Shift
keycode 105 = Control_R NoSymbol Control_R
keycode 108 = ISO_Level3_Shift Multi_key ISO_Level3_Shift Multi_key
```
The same user then posted information from
```
xev -event keyboard | grep -m 1 -A 2 "KeyPress event"
```
after pressing the control key (unclear if it was the left or right one):
```
keycode 50 (keysym 0xffe1, Shift_L)
```

The information from **xev** matches what the user is experiencing whereas the **xmodmap** information doesn't (even though other posters have the same xmodmap output). So there's a disparity between what xmodmap and xev report. How can that be explained?

---

### Post by CantankRus on 2016-10-29
Is the Keyboard faulty....coffee spill???
Test with another usb keyboard if possible.

---

### Post by Bucky Ball on 2016-10-30
> **jv10 said:**
> EDITED: It does copy and paste instantly in the browser

It works ok in the browser? Just doesn't work in a word processor file, a terminal or anywhere else??? 

If you are talking specifically about the terminal, then yes, Ctl+c will give '^C' in a terminal. Paste in the terminal is shift+ctl+v. Copy same convention: *shift*+ctl+c. 

Just thought I'd mention. You may have mentioned this earlier but thread getting fairly long. :)

---

### Post by vasa1 on 2016-10-30
OP seems to be using a gaming laptop: MSI GE70 2PE APACHE PRO. I wonder if there are some BIOS/UEFI settings that may be involved.> And, on a more practical level, the SteelSeries Engine software supplied with the GE70 gives gamers plenty of options for customizing the keyboard, selecting different colour schemes and applying macro commands to the keys of your choice.from [http://www.pcadvisor.co.uk/review/laptops/msi-ge70-2pe-apache-pro-gaming-laptop-review-3539075/](http://www.pcadvisor.co.uk/review/laptops/msi-ge70-2pe-apache-pro-gaming-laptop-review-3539075/)

---

### Post by Bucky Ball on 2016-10-30
@vasa1: There's a point. I was wondering, and going for long shots here, about setting the keyboard model in 'Keyboard'. I'm using Xubuntu-core so have no idea about Ubuntu, but if I go Keyboard> Layout tab and> Keyboard model ...

There are a heap of options in there, and just below that a drop-down list for 'Change Layout Options' which looks like it changes the function of various keys. Wonder if that has the control key set to be shift somehow. Hmm. :-k

If you find that GUI and that drop-down, it should have *nothing* in it. 'Change keyboard options' should have no selection and if it has, perhaps that's your issue.

---

### Post by vasa1 on 2016-10-30
BTW, for those interested in making CapsLock into a "hyper" key, gotbletu has a video on it: [https://www.youtube.com/watch?v=W9_H_M-H-a4](https://www.youtube.com/watch?v=W9_H_M-H-a4)

---

### Post by jv10 on 2017-02-01
Just for future reference,

Thank you all for the help I found that was the Keyboard fault even being working at the browse the I bought a new keyboard and now everything is working.

Thank you again for all the help. Sorry for reviving the post but if someone ever gets the same problem just try with a new keyboard. 

PS: old keyboard was a Chinese brand.

Regards.

---

### Post by QIII on 2017-02-01
> **jv10 said:**
> PS: old keyboard was a Chinese brand.

And how is this relevant?

---

### Post by jv10 on 2017-02-01
> **QIII said:**
> And how is this relevant?

I have no idea probably some drives are not compatible. Just wanted to let ppl know that it fixed my problem.

---

