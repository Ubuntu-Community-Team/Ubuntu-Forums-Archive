---
title: "[SOLVED] installing new fonts"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by scotcella on 2008-05-21
HI there

I want to install some specific fonts but i'm not sure about how to do it. I've tried looking up the search function but didn't find anything related to my enquiry.

FYI I have installed Hardy onto my laptop, if that's any help.

Many thanks in advance!

---

### Post by Twitch6000 on 2008-05-21
Would you be meaning the mstcorefonts?
If so go in the terminal and use this command-
```
sudo apt-get install mstcorefonts
```

---

### Post by iaculallad on 2008-05-21
Press Alt+F2 to open the run dialog box then type "fonts://" (without the quote) into the text box and click &#8220;Run&#8221;.
This would open a windows where you could copy and paste the specific font/s file to be installed.

---

### Post by scotcella on 2008-05-21
> **Twitch6000 said:**
> Would you be meaning the mstcorefonts?
If so go in the terminal and use this command-
```
sudo apt-get install mstcorefonts
```

Hi Twitch,

I'm aware of mstcorefonts..  but that's not what I'm after, I have this font file called inky dinky and would like to put it in the fonts folder.

Many thanks

---

### Post by scotcella on 2008-05-21
> **iaculallad said:**
> Press Alt+F2 to open the run dialog box then type "fonts://" (without the quote) into the text box and click “Run”.
This would open a windows where you could copy and paste the specific font/s file to be installed.

I tried this method..  there was an error popup that said 

"Nautilis cannot handle fonts: location".

What ever that means?

Thanks for both of your help.

---

### Post by BobCFC on 2008-05-21
You can put a folder in your home directory with a dot in front called  **.fonts**  and stick .ttf files in there to show up in the lists of fonts in programs


You need to goto View->Show Hidden Files to see  folders that begin with a dot.

---

### Post by Zularan on 2008-05-21
There's a .font folder in your home dir. Browse to your home dir and make sure you can see  hidden files and folders (Control-H to toggle) and open .fonts and copy the font files (*.ttf etc) in there.

---

### Post by iaculallad on 2008-05-21
Here is a [workaround]("http://www.howtodude.net/howto/view.article.php/183") with that error.

---

### Post by HotShotDJ on 2008-05-21
If you put new fonts into your .fonts directory (I recommend this as well), don't forget to open a terminal and run ```
fc-cache -vf
```This will make the fonts available to your system.

---

### Post by scotcella on 2008-05-21
Thanks everyone. 

Solved this by going to my home directory and opening the hidden files and making a new .fonts folder, and installing the fonts I wanted.

Worked a charm.

---

### Post by zaivala on 2008-05-24
> **Twitch6000 said:**
> Would you be meaning the mstcorefonts?
If so go in the terminal and use this command-
```
sudo apt-get install mstcorefonts
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package mstcorefonts
:- $

OK, so where are the mstcorefonts?

---

### Post by HotShotDJ on 2008-05-24
> **zaivala said:**
> OK, so where are the mstcorefonts?The package is msttcorefonts.

---

### Post by zaivala on 2008-05-24
My bad... missed a t.  Thanks everyone!

---

### Post by shuukazedojo on 2008-05-28
Hello all. I know this thread has been "SOLVED" but I'm having some related issues that I hope you'll be able to help with. 

FYI, running Gutsy on a desktop dual booted with XP from separate hard drives.

I downloaded some .zip files from a font site (fontfreak)...pulled the .ttf files out and dropped them into the .fonts folder I created under the home directory. After seeing that they weren't available via Open Office, I tried opening the terminal and running:

```
fc-cache -vf
```

It showed a sucess message, but still nothing in Open Office. 

What am I missing here?

Thanks in advance!!!

---

### Post by zaivala on 2008-05-28
> **shuukazedojo said:**
> Hello all. I know this thread has been "SOLVED" but I'm having some related issues that I hope you'll be able to help with. 

FYI, running Gutsy on a desktop dual booted with XP from separate hard drives.

I downloaded some .zip files from a font site (fontfreak)...pulled the .ttf files out and dropped them into the .fonts folder I created under the home directory. After seeing that they weren't available via Open Office, I tried opening the terminal and running:

```
fc-cache -vf
```

It showed a sucess message, but still nothing in Open Office. 

What am I missing here?

Thanks in advance!!!

Good question.  Is what is in Message #11 helpful?  Also, in the old days I would have asked "did you download print fonts, or just screen fonts?"

Moss

---

### Post by adobrakic on 2008-05-28
How would i download the windows fonts Arial and Times New Roman. I wanna install these because sites seem to use these fonts the most, and all of my websites' fonts look different.

---

### Post by shuukazedojo on 2008-05-28
zaivala, 

To answer your questions, what you posted in #11 did create some positive results. What I mean is, when I followed those directions, I ended up with some new fonts on the list...Micro$oft fonts, of course. As far as print fonts or screen fonts, I'm not sure. Fontfreak only gives an option to download the .zip file (or something for mac). From there I grabbed the .ttf files and dropped them into the .fonts folder I created under the home directory.

What do you think?

---

### Post by zaivala on 2008-05-28
> **adobrakic said:**
> How would i download the windows fonts Arial and Times New Roman. I wanna install these because sites seem to use these fonts the most, and all of my websites' fonts look different.

Now that's easy -- open Terminal (or Konsole) and enter the line exactly like it is in Post #11 above - except put the missing "t" in "msttcorefonts".

Moss

---

