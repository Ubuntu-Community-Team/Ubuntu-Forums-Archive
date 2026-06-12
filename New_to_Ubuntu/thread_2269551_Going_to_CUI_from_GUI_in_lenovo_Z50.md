---
title: "Going to CUI from GUI in lenovo Z50"
date: 2015-03-16
forum: New to Ubuntu
---

### Post by sunny18 on 2015-03-16
Hi All, I am new in linux. I am facing an issue in Ubuntu 14.10 version.
I am using this on my laptop Lenovo Z50. This laptop have something wrong. When I press "**Ctrl + F4**" key it take me to Ubuntu CUI and I feel like I am using Ubuntu CUI Server Edition. All task are running in background like if I had played music and Then I press "**Ctrl + F4**" on Chrome browser to close the tab then it take me to CUI and music and other thing going on in background.
Can anyone tell me how to go to GUI back? And How to disable this shortcut so I cannot go to CUI again?

Thanks
Sunny.

---

### Post by Kirboosy on 2015-03-16
Let me be the first to say welcome to the forums!

The "CUI" as you are referring to is is known as a TTY session. Generally they are accessed by Pressing "Ctrl + ALT + F1-F6" and the regular GUI session runs on "Ctrl + ALT + F7". I'm not sure why your computer is activating the TTY on just "Ctrl + F4". 

Hope that helps!
~Caboose
PS I have moved your thread to the appropriate category.

---

### Post by v3.xx on 2015-03-16
If you are running a VirtualBox session, r-ctrl + F4 would take you to console (tty).

---

### Post by sunny18 on 2015-04-08
Hi [COLOR=#DD4814][COLOR=#C61919][Caboose885]("http://ubuntuforums.org/member.php?u=900617"),[/COLOR][/COLOR]

It means if I am in TTY session and I press Ctrl + ALT + F7 then I can come back to GUI session?

Thanks
Sunny

---

### Post by sunny18 on 2015-04-08
I tried it, not working.....

---

### Post by sunny18 on 2015-04-08
Hi [COLOR=#DD4814][COLOR=#000000][v3.xx]("http://ubuntuforums.org/member.php?u=1937239"),[/COLOR][/COLOR]

No, I am not using Virtual Machine. Any other guess please?

Thanks
Sunny

---

### Post by Kirboosy on 2015-04-09
Sunny,

Can you give us more information about your computer? Such as what version/variant of Ubuntu you are running. What software you might have installed that caused this erratic behaviour.

Thanks
~Caboose

---

### Post by Holger_Gehrke on 2015-04-09
Does this only happen only with ctrl-F4 or with all function keys from 1 to 6 ? There are normally six virtual terminals assigned for text-mode tty sessions and one for the GUI.

1) After login on the TTY you could try the command 'chvt 7'. It should do the same thing as the key-combination ctrl-Alt-F7 is supposed to do.
2) Does somebody else have access to this machine ? It might just be that that person has defined 'ctrl-F4' as a keyboard shortcut to a full-screen terminal window without a menu (in gnome terminal you can get this effect by switching of the menu-bar in the 'view' menu and hitting F11). Try whether Alt-Tab switches to other windows ...

---

### Post by sunny18 on 2015-04-10
Hi all, Here is some more information.

I have Lenovo Z50 Laptop. I have installed Ubuntu 14.10 version. And here is image of my laptop keyboard.
If you see a "Fn" key after the Left "Ctrl" key, we require it to perform "F1.... F12" task. And this keyboard is very annoying. If we forget to press "Fn" and directly press "Ctrl+F4" for closing current tab then it gose to TTY session. And After that it ask me my login creds. I put those and successfully login and after then I have to restart it using "init 6". So I do not want it go to TTY session when I press "Ctrl+F4". 
[IMG]http://tech.firstpost.com/wp-content/uploads/2014/07/lenovo-laptop-z510-keyboard-2.jpg[/IMG]

Thanks
Sunny

---

### Post by sunny18 on 2015-04-10
I recently tried "[COLOR=#000000]ctrl-Alt-F7" with "Fn" and it throws me back to GUI session again. And I am very happy to see it.
The problem is mostly solved for me. But if any one can give me an idea to stop to going in TTY session so that would be very helpful for me.

Thanks
Sunny[/COLOR]

---

