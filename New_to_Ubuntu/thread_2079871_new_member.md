---
title: "new member"
date: 2012-11-02
forum: New to Ubuntu
---

### Post by mostafaomar94 on 2012-11-02
I am new to ubuntu and i want to learn how to use? it what are the most famous and useful programs? and how to use them?

---

### Post by Lars Noodén on 2012-11-02
Welcome.  

Blender has been used to make full movies and Apache serves most of the world's web pages.  But the real question is what do you want to do and what are you interested in?  There are probably applications for that.

---

### Post by evilsoup on 2012-11-02
[Here](http://www.psychocats.net/ubuntu/index) is a useful website for new Ubuntu users. If you have any more specific questions, don't hesitate to ask.

---

### Post by Kevin McCready on 2012-11-02
To get new programs I don't use Synaptic. I open a terminal with ctrl-alt-t, then I type

```
sudo apt-get update
```
then put in my password. 

If I want to install a new package I type
```
sudo apt-get install [package name]
```


audacity for recording off internet stream
jack for cd ripping 
libreoffice-writer (closer to Microsoft word functionality and much better than abiword or openoffice)
Dolphin as File Manager
clementine 
smplayer (need to install PulseAudio Volume Control and then select Sound Recorder)
leafpad (brilliant little text editor for HUGE text files)
gnumeric (spreadsheet)
ibus-pinyin (for chinese - it needed tweaking)  not ipin sw
mirage for image manipulation
clipit (so that stuff cut to clipboard buffer is available after I quit the application)
The file manager (PCManFM 0.9.9) is awful and slow (sorry guys). 
for my ctrl-alt-? keybindings I tweaked 
~/.config/openbox/lubuntu-rc.xml 
to add in the <keyboard> section: 
    <keybind key="C-A-whatever">
      <action name="Execute">
        <command>blah blah</command>
      </action>
    </keybind>

To make Desktop shortcut
```
cd Desktop
ln -s <directory where your file or program is>/<name of your file or program>

```

---

### Post by offgridguy on 2012-11-02
The most useful programs are obviously the ones dealing with the things that interest
you , but have a look in the software center and see if there's something you like. :)

---

### Post by Abhinav Kumar on 2012-11-04
> **mostafaomar94 said:**
> I am new to ubuntu and i want to learn how to use? it what are the most famous and useful programs? and how to use them?

Use help and ubuntuforums to know more. Consult chapter 1 and chapter 2 of [ here ](http://www.freeos.com/guides/lsst/) for a  good introduction.

+1 for Lars Noodén
Most  useful depends on what is most useful to you. In my opinion, Terminal and ubuntu software center are the most useful. To learn more about a command
type in terminal 
```
man commandName
```. 
For GUI commands you can see their documentation

---

### Post by kenizl86 on 2012-11-04
I hope you enjoy Ubuntu as much as I have. I don't have Ubuntu, but rather Xubuntu, as it's great for my older PCs.

I find that, for Word processing, I prefer AbiWord, as it's relatively small and is a lot like Microsoft word (if you're used to that).

For internet, Mozilla Firefox is good, but Google Chrome is much more streamlined. And (best of all), if you have a Gmail account, Chrome syncs everything from your previous accounts (if you had Internet explorer or Mozilla before Chrome), like your bookmarks and settings.

Document Viewer is really good for PDFs, and Xfburn is simple and easy for CD burning.

Also, if you switched from Windows and have EXE files you want to run, Wine is the program for that. The only drawback is that it's kinda confusing at first for newbies, so the Documentation is good for that (and running the command: "man wine" in Terminal).

Two other things, which are good for viewing information for your computer: Sysinfo, and Disk Utility.

---

### Post by newb85 on 2012-11-04
You should know, though, that WINE doesn't work for all .exe's, and even when it does, it doesn't always work well.  If there is a native Linux app that does basically the same thing, you're usually better off going that route.

---

### Post by Paari on 2012-11-05
After installing Ubuntu, I opened the Software center and checked the categories for programs. I ended up installing things which I've haven't even heard of... A nice description of each program will be provided, so that you can plan which to install....

---

