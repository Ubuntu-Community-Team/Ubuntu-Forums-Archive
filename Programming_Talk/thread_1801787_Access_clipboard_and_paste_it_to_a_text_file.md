---
title: "Access clipboard and paste it to a text file"
date: 2011-07-11
forum: Programming Talk
---

### Post by arunkumar413 on 2011-07-11
Assuming that the ubuntu clipboard has some text, i want to write a simple python program to access the clipboard content and paste them into a text file. 
please help me.

---

### Post by Zugzwang on 2011-07-11
Apparently, you don't even need to write a Python program for that. See for example [this blog post]("http://www.pgrs.net/2008/1/11/command-line-clipboard-access") for details.

If this solution is not the right one for you (which it might not, as this blog post was easy to find using a google search, so you might have seen it as well), please explain why.

---

### Post by arunkumar413 on 2011-07-13
xsel works only from command line. That is not what i'm looking for.What i want to do is to create a program in python that monitors the clipboard and when i press a keyboard shorcut key the clipboard content should be pasted into  a text file.

My program when executed will run in the background and waits for the hot key to be pressed. If the hotkey is pressed then it should paste the clipboard content to a text file.

Thanks

---

### Post by Vaphell on 2011-07-13
where is the problem? write a script and set up a hotkey for it - results will be the same.

this is about the opposite problem (hotkey pasting content of a file to the current cursor location)
[http://ubuntuforums.org/showpost.php?p=10975049&postcount=6](http://ubuntuforums.org/showpost.php?p=10975049&postcount=6)

---

### Post by TwoEars on 2011-07-13
You will need to look into the gtk module.
Read this  - [http://www.pygtk.org/docs/pygtk/class-gtkclipboard.html](http://www.pygtk.org/docs/pygtk/class-gtkclipboard.html)

HTH.

---

### Post by dwhitney67 on 2011-07-13
> **arunkumar413 said:**
> xsel works only from command line. That is not what i'm looking for.What i want to do is to create a program in python that monitors the clipboard and when i press a keyboard shorcut key the clipboard content should be pasted into  a text file.

My program when executed will run in the background and waits for the hot key to be pressed. If the hotkey is pressed then it should paste the clipboard content to a text file.

Thanks

You do not need a Python program to do this.  On my system, once text is in the clipboard, I can use the right-mouse button to launch a menu where I can then select "Paste" so that the clipboard contents are copied to the destination text file.  Anyhow, I'm sure that your system is the same.

If you wish to create "hot-keys" to perform the copy and pasting of keys that may be doable, but do bear in mind that different applications accept different keystrokes that would need to be emulated.  For example, in Gedit, ctrl-v is for pasting, whereas in gnome-terminal, ctrl-shift-v is required.

In conclusion, unless you have a compelling reason to implement this Python project, I would abandon it in favor of existing system capabilities.

---

### Post by arunkumar413 on 2011-07-13
> **dwhitney67 said:**
> You do not need a Python program to do this.  On my system, once text is in the clipboard, I can use the right-mouse button to launch a menu where I can then select "Paste" so that the clipboard contents are copied to the destination text file.  Anyhow, I'm sure that your system is the same.

I dont like to switch the window to do a paste. I want to paste from the same widndow where i copied.

---

### Post by dwhitney67 on 2011-07-13
> **arunkumar413 said:**
> I dont like to switch the window to do a paste. I want to paste from the same widndow where i copied.

The "from" is your source (ie. the window where you copy data); the "to" is your destination (e.g. text file).  Where are you specifying the destination in this "magical" operation that you want to perform?

---

### Post by Vaphell on 2011-07-13
if you want to dump highlighted text to some file:
goto hotkeys configuration in preferences
add your custom hotkey, let's say ctrl+f12
in command enter
```
sh -c 'xsel -o >> /home/yourname/whatever.txt'
```

now ctrl+f12 should append highlighted selection to whatever.txt

---

### Post by arunkumar413 on 2011-07-14
> sh -c 'xsel -o >> /home/yourname/whatever.txt'

But i would like to extend that for copying and pasting  images also.

---

### Post by Vaphell on 2011-07-14
how exactly does one paste images into a text file?

---

### Post by yuler on 2011-08-26
I solved a similar problem using xclip, which is a CLI utility that can read/write the X clipboard. 

Images have headers embedded in their data stream that identify the filetype, so saving an image is as easy as selecting an image, copying to the clipboard, and saving the clipboard to a file.  If you want your hotkey to do any wizardry such as recognizing filetypes to apply automatic filename extensions, or parsing multiple selected images, it should call a script that scans the clipboard for known filetypes and apply the rules according to what it finds before it writes the file.

---

