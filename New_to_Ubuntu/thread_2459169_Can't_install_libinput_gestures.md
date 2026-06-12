---
title: "Can't install libinput gestures"
date: 2021-03-12
forum: New to Ubuntu
---

### Post by dollfish on 2021-03-12
Hello everyone,

I'm new to Ubuntu and I'm running it on a partition. It is 20.04 and I'm trying to install libinput gestures.
I keep getting this message when trying to install the interface: **python3: can't open file 'setup.py': [Errno 2] No such file or directory**

Also, my gestures are configured but the webpage back/forward swipes are reversed. I don't know how to fix that.

Do I have to use terminal for everything on Ubuntu? I don't think I can learn how to use it if that is the case and I might ditch and go back to using my mac unfortunately, which I don't want because my mac laptop is very old.

Thank you very much!

:mrgreen:

---

### Post by Impavidus on 2021-03-12
> **dollfish said:**
> Hello everyone,

I'm new to Ubuntu and I'm running it on a partition. It is 20.04 and I'm trying to install libinput gestures.
I keep getting this message when trying to install the interface: **python3: can't open file 'setup.py': [Errno 2] No such file or directory**

Also, my gestures are configured but the webpage back/forward swipes are reversed. I don't know how to fix that.Have you got a link to whatever instructions you followed to install this? The script interpreter python3 fails to run the setup script, which could be as simple as failure to change to the right directory before running the command. I haven't tried this myself though. It's bad enough I sometimes have to use gestures on my phone.

> Do I have to use terminal for everything on Ubuntu? I don't think I can learn how to use it if that is the case and I might ditch and go back to using my mac unfortunately, which I don't want because my mac laptop is very old.

Thank you very much!

:mrgreen:
You don't have to use terminal for everything, or even for anything, just as you don't have to use manual shifting in a sports car, but you may prefer it anyway. If you're happy with a web browser and a WYSIWYG writing tool, there's no need for the terminal. If you want live satellite images as wallpaper on your desktop, craft really beautiful documents with lots of macros, create your own solar system simulator, run your home media server or fix the system after you broke it (which is easy, using the terminal), some terminal skills will be handy.

On the forum we often use the terminal. It's much easier to tell "Run these commands and post the output" than "Click on the first button from the left, then open the second tab, toggle the fourth box, click OK and post a screenshot of the error message." What's more, there are many different GUIs available for Linux, but the command line interface is much more uniform. Servers usually have no GUI at all.

---

### Post by dollfish on 2021-03-12
Thank you very much for your reply. I've downloaded the following and here are the instructions. I seem to have installed the gestures but I haven't been able to install the interface. I get the error that I mentioned at the last step.
Libinput-Gestures Link: [https://github.com/bulletmark/libinpu...]("https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqa3REUXhDZ2dad0wzckxpSkpqMmlobmFYSTJUd3xBQ3Jtc0tsTzNuSzFWWFNfY3VrdDlrUVJuLTJsdXllLWxKbGJZUGZTSHNYYmJtWTRmdEJlWnZVbXFHbmN6WVN4R2FMZm92WkZJOV9JMUl2ZXdpZGtoaU1nbG5JZWRhSHh0Y1NiTXY0SkxBbWdsRjI4YjU5bHJTMA&q=https%3A%2F%2Fgithub.com%2Fbulletmark%2Flibinput-gestures")&#8203; 
Gestures App Link: [URL="https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbUlFTUNlU2wzUWxLV3d4bVlOM19weVpuTE9Nd3xBQ3Jtc0trVktiVlVNYnV0VW9rZGl5SGJYamlRSUc5MDJ4eWI0Z0d6bmhvYWNkSUFnSzBhaXBfeGpkeUJHTFhIdWpKZ3VabzkxbG81ejJEMEpBZy1NM0MxYlRnUDBvOS1sXzZJNFB1Vk5WdG9qZlZqN3pTNHhmSQ&q=https%3A%2F%2Fgitlab.com%2Fcunidev%2Fgestures"]https://gitlab.com/cunidev/gestures

[/URL][COLOR=#800080]sudo gpasswd -a $USER input

Restart after this

sudo apt-get install wmctrl python3 python3-setuptools xdotool python3-gi libinput-tools python-gobject

cd Downloads/libinput-gestures-master sudo make install

libinput-gestures-setup autostart libinput-gestures-setup start

cd Downloads/gestures sudo python3 setup.py install
[/COLOR]

---

### Post by Holger_Gehrke on 2021-03-12
From the text on [https://github.com/bulletmark/libinput-gestures:](https://github.com/bulletmark/libinput-gestures:)
> NOTE: If you don't use "natural" scrolling direction for your touchpad then you may want to swap the default left/right and up/down configurations.
To fix this problem copy the system wide configuration file /etc/libinput-gestures.conf to the hidden configuration directory in your home directory 'cp /etc/libinput-gestures.conf ~/.config/' then edit that file 'nano ~/.config/libinput-gestures.conf'. Find the lines beginning with 'gesture swipe right' and 'gesture swipe left' and change 'left' to 'right' and vice versa. Hit 'strg-o' to save and 'strg-x' to exit the editor. Stop and restart libinput-gestures with 'libinput-gestures-setup stop;libinput-gestures-setup start' to make it read the new configuration.

The gestures configuration GUI seems to have changed quite a bit since whatever tutorial you're following was written. It doesn't use the standard python setup tools anymore, now it needs the build systems meson and ninja for installation. Both should be available from the repositories. The instructions on [https://gitlab.com/cunidev/gestures/](https://gitlab.com/cunidev/gestures/) should be current

The author of libinput-gestures sees the program as a temporary fix until the major Desktop Environments support gestures natively. It's basically only for people who simply can't live without gestures, even if they don't work all that well (on my system the diagonal swipes don't seem to get recognized at all and the others never work on the first try ...)

And *please*, don't drag and drop links from youtube videos into forum posts. Those links point at youtube's redirector, it's kind of hard to tell tell where they actually go and they first send you to youtube and and ask you if you want to leave youtube when you actually never wanted to go there ...

Holger

---

### Post by dollfish on 2021-03-13
Thank you for your reply, unfortunately I don't know how to do the change that you mentioned. I don't understand terminal commands, could you explain to me how to make this change?

I didn't know that the links would go to Youtube first so apologies for that.

Also, I did follow the instructions on [https://gitlab.com/cunidev/gestures/](https://gitlab.com/cunidev/gestures/) with no avail. I think at this point I just want to have the forward / back direction corrected. It seems that the other things are way too advanced for me at this point. I've also managed to install a couple of themes and set up drag lock, which I feel proud about! :KS

---

### Post by dollfish on 2021-03-13
Yayyy!! Took me about an hour but I managed to fix the forward / back situation!! I'm ecstatic! By doing this, I think I may now be able to configure some gestures without the need for the interface. Now I need to figure out how to keep "drag lock" from stopping working at random times.

---

### Post by Holger_Gehrke on 2021-03-13
Good for you. According to this [discussion on AskUbuntu]("https://askubuntu.com/questions/1238551/drag-lock-not-working-on-fresh-20-04-install") the drag lock problem is a non-configurable timeout of 300 ms between tap and drag. If you're just minimally to slow it doesn't work and as of now there's no way to change it.

Holger

---

### Post by dollfish on 2021-03-15
I have followed these instructions on the page you linked:

Install synaptics with sudo apt install xserver-xorg-input-synaptics , restart.

  Then synclient LockedDrags=1 and it should work.

It does work but only until I shut down my computer or maybe when I log out, I'm not sure. Is there a way to keep it in effect indefinitely?

---

### Post by Holger_Gehrke on 2021-03-15
There's a reason why that answer at AskUbuntu has 0 votes: the Synaptics driver is very old code, originally a driver for one specific early touchpad by one specific manufacturer connected in one specific way. Over the years it's been hacked again and again to include other interfaces, other devices by other manufacturers and multitouch. Depending on what else you've got in your system installing it can lead to situations in which none of your input devices work. AFAIK nobody works on it anymore and it's probably going to go away in the near future. Had I noticed this answer in there I would have cautioned you against trying it. Nice for you that it works, but that was risky.

Back when I used synaptics - in Ubuntu 12.04, I think - there were additional options available in the mouse settings if you used that driver. Check whether that's still the case, maybe you can just put a mark in a check box and be done with it.

If that's not the case then the easy way to having that setting always active is to put a desktop file in '~/.config/autostart/' which will execute that command when you log in. Open your favourite text editor, cut and paste this block
```

[Desktop Entry]
Encoding=UTF-8
Version=0.9.4
Type=Application
Name=Set LockedDrags
Exec=synclient LockedDrags=1
StartupNotify=false
Terminal=false
Hidden=false

```
and save it as '~/.config/autostart/setLockedDrags.desktop'. 

Holger

---

