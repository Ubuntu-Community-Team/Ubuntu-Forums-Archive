---
title: "Just Installed Ubuntu, Have a Few Questions"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by SpydersWebbing on 2011-12-30
So I installed Ubuntu as the sole operating system on my computer, and I've run into a few snags. I'm using a Compaq laptop that was originally designed for Windows Vista. The wireless seems to work just fine, and the computer starts up extremely quickly.

1. The computer sometimes freezes up, and the screen becomes darker. I generally can't do anything until the screen brightens up again. This usually happens if I try to do more than three things at once, but it can come at any time.

2. I can't use my microphone or webcam anymore. Is there any software I can install to fix that problem?

3. My DVD player seems to have stopped working, because it lost its decoder. Any special place I can find something, or will any decoder do?

Thanks in advance for your help!

Nathan

EDIT: I'm running 11.10

---

### Post by NilPointer on 2011-12-30
> **SpydersWebbing said:**
> So I installed Ubuntu as the sole operating system on my computer, and I've run into a few snags. I'm using a Compaq laptop that was originally designed for Windows Vista. The wireless seems to work just fine, and the computer starts up extremely quickly.

1. The computer sometimes freezes up, and the screen becomes darker. I generally can't do anything until the screen brightens up again. This usually happens if I try to do more than three things at once, but it can come at any time.

2. I can't use my microphone or webcam anymore. Is there any software I can install to fix that problem?

3. My DVD player seems to have stopped working, because it lost its decoder. Any special place I can find something, or will any decoder do?

Thanks in advance for your help!

Nathan

EDIT: I'm running 11.10

1. As I understand, processes becoming "unresponsive" and their windows darkens. That might occur on slow machines. (That's just like Windows adds "(Not responding)" to not responding app's window header).

2. Did you try configure mic with alsamixer?

3. I don't understand what you mean. Ubuntu should play DVD Video well.

---

### Post by SpydersWebbing on 2011-12-30
1. I kinda figured. It happens a lot, though. Is there anything I can do to tweak the performance? I suspect it might have something to do with the graphics, but I can't tell for sure. 

2. Didn't know it existed. I'll download it and give it a look, and let you know what happens.

3. Strange. I'll insert another DVD and reply after I've done that.

---

### Post by Jahid65 on 2011-12-30
2 Click on the sound icon on right top. Go to sound settings > Input & check your settings. Open gnome-recorder to record something & then playback.
3 you need to install libdvdcss2, w32codec & some gstreamer codec.

---

### Post by wolfen69 on 2011-12-30
For DVD playback and all codecs, do
```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then
```
sudo apt-get install non-free-codecs libdvdcss2
```
alsamixer is already installed, do
```
alsamixer
```

---

### Post by grahammechanical on 2011-12-30
When we install Ubuntu we are given the option to install some proprietary codexs (codices before anyone points that out). Did you tick the box? (If not then you can install Ubuntu restricted Extras from the software centre.

Ubuntu does not install proprietary software by default. But it does make it easy for the user to install such software if that is the users choice.

If an application windows is greying out then that is due to limited memory for the processes being run at the time.

Regards.

---

### Post by SpydersWebbing on 2011-12-30
> **wolfen69 said:**
> For DVD playback and all codecs, do
```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```then
```
sudo apt-get install non-free-codecs libdvdcss2
```alsamixer is already installed, do
```
alsamixer
```

Unforunately I'm brand-new to coding, where do I do an input?

Or did I completely miss the point?

So can the graying out problem be solved? Completely new with computer stuff, but more than willing to learn!

---

### Post by chipbuster on 2011-12-30
You can either use Terminal Emulator (access with CTRL+ALT+T in gnome) or you can switch to a virtual terminal by pressing CTRL+ALT+F(number). F1 through F6 will land you with text-only terminals, F7 will get you back to the window display.

To copy or paste in the terminal emulator (CTRL+ALT+T), you need to use CTRL+SHIFT+C and CTRL+SHIFT+V, since the regular CTRL+C and CTRL+V are used for other things.

---

### Post by gamblor01 on 2011-12-30
> **chipbuster said:**
> You can either use Terminal Emulator (access with CTRL+ALT+T in gnome) or you can switch to a virtual terminal by pressing CTRL+ALT+F(number). F1 through F6 will land you with text-only terminals, F7 will get you back to the window display.

To copy or paste in the terminal emulator (CTRL+ALT+T), you need to use CTRL+SHIFT+C and CTRL+SHIFT+V, since the regular CTRL+C and CTRL+V are used for other things.


You can also hit your Windows key (referred to as the "Super" key) and then just starting typing the word terminal.  Then select the option that it finds and it will launch it.

Welcome to Ubuntu and Linux!  Ask if you have any further questions, and learn to love the terminal -- it will make life so much better.  :)

---

### Post by gordintoronto on 2011-12-30
It can be helpful if you describe your computer: CPU, memory, video adapter.

For the webcam, open Software Center and install Cheese. Run it and tell us if your webcam works.

In 95% of cases when "the microphone doesn't work," it is muted.

---

### Post by morhin on 2011-12-31
I'm new to this too so I can't add much to the conversations except......

I've found a book that has been incredibly helpful in my getting started. 

It's Ubuntu for Non-Geeks 4th edition (for 10.04). It might help you get rolling. It's by Rickford Grant and Phil Bull.

I'd call it a pretty good primer for us first day in school noobies.

morhin

my wife tells me I'm wrong so often I'm thinking about becoming a weatherman

---

### Post by flyfishingphil on 2011-12-31
Just to make it easy to gain access to various points here are some easy to follow "trails".

Somewhere on your screen there is a toolbar that shows Applications, Places, System. This is the starting point.

For Terminal, (to do the sudo apt-get, or other Sudo action):

Click on Applications > click on Accessories > Click on Terminal. This will bring you to the terminal window that opens and you can now start entering info like sudo apt-get

Another source for programs, etc, is Synaptic. For this

System > Administration > Synaptic Systems Manager > enter your password (if set up) and do the search for what you are looking for. 

Hope this helps in making it easier to get around.

FYI: My modem/router is connected to the outlet but my laptop is using WiFi to connect to the router/modem. No problems in doing downloads or connecting to anything on the Net using Ubuntu 11.04.

---

### Post by mastablasta on 2011-12-31
just to make sure - you can copy the commands you were give into the terminal (often new people type them which can bring new problems as small typing error can change a lot). otherwise everything you were told can be done in graphical user interface.

Additionally to get information abotu your system you can pu tthis command into terminall:

```
sudo lshw
```you can then post results here so we can see what hardware you have.
note that command will require you to put in your user password. you won't see anythign being typed not even asterisks (which is this sign: *).

to get only the graphics card you can copy this into terminal:
```
lspci | grep VGA
```see more info on how to get good help faster here: 
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

