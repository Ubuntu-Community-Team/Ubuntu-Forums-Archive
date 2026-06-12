---
title: "No obvious touchpad settings in Lubuntu"
date: 2015-08-16
forum: New to Ubuntu
---

### Post by AbleTassie on 2015-08-16
I want to double tap the touchpad and open desktop icon programs. I cannot do this now, I have to put the cursor on the icon using the touchpad, then use the right click touchpad button, then select "Open" on the drop down menu. I want to change the touchpad settings. But I do not have any obvious touchpad settings under "Preferences." Nothing under Keyboard and mouse, nothing under keyboard and input method, nothing under input methods.

I am using Lubuntu 14.04.3 LTS

Am I missing something?

Thanks,

A.

---

### Post by Geoffrey_Arndt on 2015-08-16
> **AbleTassie said:**
> I want to double tap the touchpad and open desktop icon programs. I cannot do this now, I have to put the cursor on the icon using the touchpad, then use the right click touchpad button, then select "Open" on the drop down menu. I want to change the touchpad settings. But I do not have any obvious touchpad settings under "Preferences." Nothing under Keyboard and mouse, nothing under keyboard and input method, nothing under input methods.

I am using Lubuntu 14.04.3 LTS

Am I missing something?

Thanks,

A.

See here:   [URL="https://www.youtube.com/watch?v=QKhxT5AHqP4"]https://www.youtube.com/watch?v=QKhxT5AHqP4

[/URL]

---

### Post by AbleTassie on 2015-08-17
Thanks Geoffrey,

I followed the instructions in the video successfully and installed synaptics. But I do not see how to change the settings in the Gpointing devices settings to enable double tapping of the touchpad to open an icon program by double tapping the touchpad. When I move the cursor arrow over the icon using the touchpad and double tap the touch pad, nothing happens. And I do not see how to change this to make the underlying program open.

A.

---

### Post by Geoffrey_Arndt on 2015-08-17
So, just to be clear, you do have a standard Synaptics (SYN/PS2) Touchpad . . . your model being one with a left and right button at the bottom of the touchpad?    

When you use the touchpad to move the cursor over an application icon on your desktop . . . and then you "double-click" the left mouse button, the program doesn't open?   

Double tapping the main area of the touchpad is different than double-clicking the left touchpad button.    Regarding usefulness or functionality . . . a double click of left touchpad button OR even, a single click of that button AND then just pressing the enter key . . . will all accomplish the desired effect (to open the app).

I don't use Lubuntu (never have), but I recall that Kubuntu (with KDE) will allow the user to set the mouse or touchpad so you can highlight any desktop app by scrolling over it, and then either a "single-mouse click" or "single touchpad left button click" will open the app.   I really preferred that over anything else (except hot-keys of course) for speed and simplicity.   So, is there any compatible setting in the Lubuntu desktop for mouse/touchpad "single-click" option??

Note:  to quickly confirm you have a standard Synaptics touchpad, you can do this:

>   open a terminal (ctrl+alt+t)
>   input the following "xinput -list"

the output should provide the info re your touchpad, (and eliminate another type such as Alps)

---

### Post by AbleTassie on 2015-08-17
> **Geoffrey_Arndt said:**
> So, just to be clear, you do have a standard Synaptics (SYN/PS2) Touchpad . . . your model being one with a left and right button at the bottom of the touchpad?    [QUOTE]

YES


[QUOTE=Geoffrey_Arndt;13340094]When you use the touchpad to move the cursor over an application icon on your desktop . . . and then you "double-click" the left mouse button, the program doesn't open?   [QUOTE] 

NO INCORRECT IT DOES OPEN

[QUOTE=Geoffrey_Arndt;13340094] Double tapping the main area of the touchpad is different than double-clicking the left touchpad button.    Regarding usefulness or functionality . . . a double click of left touchpad button OR even, a single click of that button AND then just pressing the enter key . . . will all accomplish the desired effect (to open the app).[QUOTE] 

YOU ARE CORRECT, USING THE BUTTONS AS YOU DESCRIBE OPENS THE APPLICATIONS

[QUOTE=Geoffrey_Arndt;13340094] I don't use Lubuntu (never have), but I recall that Kubuntu (with KDE) will allow the user to set the mouse or touchpad so you can highlight any desktop app by scrolling over it, and then either a "single-mouse click" or "single touchpad left button click" will open the app.   I really preferred that over anything else (except hot-keys of course) for speed and simplicity.   So, is there any compatible setting in the Lubuntu desktop for mouse/touchpad "single-click" option?? [QUOTE]

I DON'T SEE ANYTHING LIKE THAT

[QUOTE=Geoffrey_Arndt;13340094] Note:  to quickly confirm you have a standard Synaptics touchpad, you can do this:

>   open a terminal (ctrl+alt+t)
>   input the following "xinput -list"

the output should provide the info re your touchpad, (and eliminate another type such as Alps)

YES"SynPS/2 Synaptics touchpad" COMES UP

---

### Post by Geoffrey_Arndt on 2015-08-17
OK, here is the obvious question that should have been confirmed from the first . . . 

??  Did you enable tapping via the System Settings>Mouse & Touchpad>Touchpad "Tap to Click" button?   I've done that and it works better than I thought, as I can use the touchpad to move cursor to a program icon, or a web page button, or a windows selection button, and it selects the item and _invokes the same action as a left mouse click via a single-tap_.    Some applications may be written such that they require a double tap, but tapping does work in Ubuntu . . . :p

Perhaps a Lubuntu user that's reading these forums can comment further (as your Systems Setting options window may be different than mine).

---

### Post by AbleTassie on 2015-08-18
> **Geoffrey_Arndt said:**
> OK, here is the obvious question that should have been confirmed from the first . . . 

??  Did you enable tapping via the System Settings>Mouse & Touchpad>Touchpad "Tap to Click" button?   I've done that and it works better than I thought, as I can use the touchpad to move cursor to a program icon, or a web page button, or a windows selection button, and it selects the item and _invokes the same action as a left mouse click via a single-tap_.    Some applications may be written such that they require a double tap, but tapping does work in Ubuntu . . . :p

Perhaps a Lubuntu user that's reading these forums can comment further (as your Systems Setting options window may be different than mine).

Geoffrey,

Thanks, but I do not have the settings in Lubuntu that you describe. There are some settings regarding tapping in the newly installed Gpointing Device Settings utility (referred to in the link you sent me). But I do not see how to set these to make a doubletap equivalent to a double click of a left touchpad button. I was able to "doubletap" in the past.

A.

---

### Post by Geoffrey_Arndt on 2015-08-18
AbleTasie, 

I ran a live version (on usb-flash-stick) last nite so I see what your're saying about a lack of graphical options to change the touchpad operation.   I do know for sure Linux (including Lubuntu) supports all Synaptics touchpad features (for some reason, double-tap is disabled by default).

I'll continue to do some research, but your best bet now is to get the attention of an experienced Lubuntu user.  I'll continue to check for a simple solution (I know it can be done via the command line but I hesitate to make a suggestion unless I know the source and it's a "recent" fix (not one going back to 2012 or earlier where the process/files may be different).

So double-clicking the left touchpad button or using a standard mouse may have to be your temporary work-around (have you tried Ubuntu Mate or Xubuntu as a Live CD (or usb stick) to see if that would be another option)??

I'll keep checking around meanwhile.

---

### Post by AbleTassie on 2015-08-20
> **Geoffrey_Arndt said:**
> AbleTasie, 

I ran a live version (on usb-flash-stick) last nite so I see what your're saying about a lack of graphical options to change the touchpad operation.   I do know for sure Linux (including Lubuntu) supports all Synaptics touchpad features (for some reason, double-tap is disabled by default).

I'll continue to do some research, but your best bet now is to get the attention of an experienced Lubuntu user.  I'll continue to check for a simple solution (I know it can be done via the command line but I hesitate to make a suggestion unless I know the source and it's a "recent" fix (not one going back to 2012 or earlier where the process/files may be different).

So double-clicking the left touchpad button or using a standard mouse may have to be your temporary work-around (have you tried Ubuntu Mate or Xubuntu as a Live CD (or usb stick) to see if that would be another option)??

I'll keep checking around meanwhile.

Thank you Geoffrey. No I have not tried Ubuntu Mate or Xubuntu as a live CD. I am not sure what you are suggesting here, booting off a live CD instead of the hard drive? I wonder how I can get the attention of an experienced Lubuntu user, any thoughts?

A.

---

### Post by yetimon_64 on 2015-08-20
> **AbleTassie said:**
> ... I wonder how I can get the attention of an experienced Lubuntu user, any thoughts?

A.

You could edit your thread title and add the "lubuntu" tag to the title so helpers in the forum see it more so as an lubuntu issue. Cheers, yeti. 

(Note, if for any reason you can't change the title yourself, hit a "report post" link in any of the posts in the thread and ask the staff to help you out to do so.)

---

### Post by lisati on 2015-08-21
*Thread title changed and **lubuntu** tag added*

---

### Post by Geoffrey_Arndt on 2015-08-21
Additional info on editing touchpad configuration settings:  (might try value of "180" for max tap time as a starting point)  (config file located in /home directory (is a hidden file - - see link two below).

[http://manpages.ubuntu.com/manpages/vivid/en/man1/synclient.1.html](http://manpages.ubuntu.com/manpages/vivid/en/man1/synclient.1.html)

[URL="https://help.ubuntu.com/community/Lubuntu/Mouse"]https://help.ubuntu.com/community/Lubuntu/Mouse


[/URL]

---

### Post by vasa1 on 2015-08-21
As background information, what is the terminal output of *xinput list*?

On my laptop running Lubuntu 14.04, I see this:

```
06:46 PM ~ $ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PixArt USB Optical Mouse                	id=11	[slave  pointer  (2)]
&#9116;   &#8627; ALPS PS/2 Device                        	id=13	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; HID 413c:8161                           	id=9	[slave  keyboard (3)]
    &#8627; Integrated_Webcam_1.3M                  	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=15	[slave  keyboard (3)]
06:47 PM ~ $ 
```
If I run *xinput --disable 14*, the touchpad is totally disabled. *xinput --enable 14* re-enables the touchpad.

=====================

Do you have a file called *~/.gtkrc-2.0.mine*? If you do, what are its contents? Does it have a line like *gtk-double-click-time=1000*?

The purpose of that line is to set the time in milliseconds between clicks. Two clicks within 1000 milliseconds will be regarded as a *double-click*. Two clicks more than 1000 milliseconds apart will be regarded as two separate *single clicks*.

If you don't have *~/.gtkrc-2.0.mine*, you can create this (empty) file by running touch *~/.gtkrc-2.0.mine*.

Either way, just add the line *gtk-double-click-time=1000* to the file using Leafpad (or any other plain text editor). If you run *file .gtkrc-2.0.mine*, you should get *.gtkrc-2.0.mine: ASCII text* as the response.

After that's done, see if double-clicking your touchpad main area (not the touchpad's left or right buttons) functions to open apps on your desktop or files in your file manager.

---

### Post by AbleTassie on 2015-08-22
> **vasa1 said:**
> As background information, what is the terminal output of *xinput list*?

On my laptop running Lubuntu 14.04, I see this:

```
06:46 PM ~ $ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PixArt USB Optical Mouse                    id=11    [slave  pointer  (2)]
&#9116;   &#8627; ALPS PS/2 Device                            id=13    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; HID 413c:8161                               id=9    [slave  keyboard (3)]
    &#8627; Integrated_Webcam_1.3M                      id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=15    [slave  keyboard (3)]
06:47 PM ~ $ 
```
If I run *xinput --disable 14*, the touchpad is totally disabled. *xinput --enable 14* re-enables the touchpad.

=====================

Do you have a file called *~/.gtkrc-2.0.mine*? If you do, what are its contents? Does it have a line like *gtk-double-click-time=1000*?

The purpose of that line is to set the time in milliseconds between clicks. Two clicks within 1000 milliseconds will be regarded as a *double-click*. Two clicks more than 1000 milliseconds apart will be regarded as two separate *single clicks*.

If you don't have *~/.gtkrc-2.0.mine*, you can create this (empty) file by running touch *~/.gtkrc-2.0.mine*.

Either way, just add the line *gtk-double-click-time=1000* to the file using Leafpad (or any other plain text editor). If you run *file .gtkrc-2.0.mine*, you should get *.gtkrc-2.0.mine: ASCII text* as the response.

After that's done, see if double-clicking your touchpad main area (not the touchpad's left or right buttons) functions to open apps on your desktop or files in your file manager.
  
Thanks Vasa (and Geoffrey),

I searched for a file called "gtkrc-2.0mine" but I can't find it           

If I run, "*file .gtkrc-2.0.mine*" I get ".gtkrc-2.0.mine: ERROR: cannot open `.gtkrc-2.0.mine' (No such file or directory)"

I ran "touch *~/.gtkrc-2.0.mine*" and then "*/.gtkrc-2.0.mine*" and I get ".gtkrc-2.0.mine: empty"
 
So now I appear to have the file, but it is empty. I am presently searching for the file using the "Find Files" tool, but it has not come up after over 20 minutes of searching. If I find it, I will try to add the line "*gtk-double-click-time=1000*" to it using a plain text editor. Is there any way to open the file using command line terminal commands?

A.

---

### Post by vasa1 on 2015-08-22
> **AbleTassie said:**
> ...
 
So now I appear to have the file, but it is empty. I am presently searching for the file using the "Find Files" tool, but it has not come up after over 20 minutes of searching. If I find it, I will try to add the line "*gtk-double-click-time=1000*" to it using a plain text editor. Is there any way to open the file using command line terminal commands?

A.
It is a hidden file because of the "." in the front. Hidden files can be made visible by pressing *Control+h* at the same time in your file manager or by using *ls -a* instead of *ls* in your terminal.

If you run
```
echo "gtk-double-click-time=1000" > ~/.gtkrc-2.0.mine
``` there's nothing else you need to do.

Edit: I never ever used the "Find Files" tool.

---

### Post by AbleTassie on 2015-08-22
> **vasa1 said:**
> It is a hidden file because of the "." in the front. Hidden files can be made visible by pressing *Control+h* at the same time in your file manager or by using *ls -a* instead of *ls* in your terminal.

If you run
```
echo "gtk-double-click-time=1000" > ~/.gtkrc-2.0.mine
``` there's nothing else you need to do.

Edit: I never ever used the "Find Files" tool.

Thanks Vasa,

I ran echo "gtk-double-click-time=1000" > ~/.gtkrc-2.0.mine in terminal & restarted the PC, but I can still double tap over an icon and nothing happens. Maybe if I increased 1000 to 2000 that would help. By the way, if I run xinput list, I get the output below:[I]

 Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Lenovo Easy Camera                          id=9    [slave  keyboard (3)]
    &#8627; Ideapad extra buttons                       id=10    [slave  keyboard (3)]
    &#8627; Asus Laptop extra buttons                   id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]


[/I]Thanks, 

A.

---

### Post by vasa1 on 2015-08-22
> **AbleTassie said:**
> Thanks Vasa,

I ran echo "gtk-double-click-time=1000" > ~/.gtkrc-2.0.mine in terminal & restarted the PC, but I can still double tap over an icon and nothing happens. Maybe if I increased 1000 to 2000 that would help. ...
Possibly. To do so just change 1000 to 2000 and rerun the command. The older version will br overwritten. If that still doesn't help, I'm out of suggestions.

BTW, where exactly are you double-tapping? It should on the main area of the touchpad, not on either button.

What is your laptop model? Maybe someone familiar with it may suggest something.

---

### Post by AbleTassie on 2015-08-22
Hi Vasa,

I ran the terminal command to increase to 2000, it did not help, even after restarting the PC. The PC is a Lenovo Y510. I think it is an Ideapad Notebook. I am double tapping right in the middle of the touchpad. The cursor moves when I use the touch pad and some actions occur with a single tap. But, not double tapping. Double tapping always worked with my previous laptop.

Thanks for your help (I have added to your Latin below).

A.

*de gustibus et coloribus non est disputandum, ***sed quandoque software simpliciter non operatur**

---

### Post by vasa1 on 2015-08-22
Just one more point ... do you have a Live CD or Live USB of any Ubuntu flavor (or do you dual-boot with windows)? Using another OS will help indicate 
whether you have a hardware issue
or
if some changes you've made have disabled the double-tap feature

And, I don't know what I'm talking about here, but is it possible that there's some setting that needs to be tweaked in your BIOS or whatever else (UEFI)?

Double-tap works by default in Lubuntu. Have you looked at [https://help.ubuntu.com/community/Lubuntu/Mouse#Touchpad_settings](https://help.ubuntu.com/community/Lubuntu/Mouse#Touchpad_settings)

And here's a thread of other users having difficulties with their touchpad: [http://ubuntuforums.org/showthread.php?t=2244958](http://ubuntuforums.org/showthread.php?t=2244958)

---

### Post by AbleTassie on 2015-08-25
In a strange twist, I have discovered that triple tapping on the touchpad opens desktop icons. I tried setting the click time up as high as 400 ms, but it did not seem to help double tap. But as I said, I can triple tap and that seems to open desktop icons. 

If I try to disable the touchpad by using the command ~$ @syndaemon -d -t

[B]I get back:
[/B]
No command '@syndaemon' found, did you mean:
 Command 'syndaemon' from package 'xserver-xorg-input-synaptics' (main)
@syndaemon: command not found

So I have enabled "palm detection" and for the least pressure and the greatest width under Preferences>pointing devices. But as I was typing this edit, the cursor jumped. So maybe it will not work that well.  
                                             
Thanks,

A.

---

### Post by AbleTassie on 2015-08-25
I am going to mark this thread as SOLVED, since I have come up with a satisfactory solution.

Thanks to everybody,

Able

---

