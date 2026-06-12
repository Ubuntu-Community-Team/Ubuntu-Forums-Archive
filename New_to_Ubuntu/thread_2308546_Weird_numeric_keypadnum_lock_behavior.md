---
title: "Weird numeric keypad/num lock behavior"
date: 2016-01-04
forum: New to Ubuntu
---

### Post by florian14 on 2016-01-04
This is under XFCE, i had to switch over from Unity because it's a VM and i'm working on it via XRDP. But i dont think my problem is actually related to that.

My numeric keypad does not work correctly with every application. Namely Sublime Text 3 and Oracle SQL Developer. Every other application is fine.

If i turn on Num lock and try to use the numeric keys in those two applications, it acts as if num lock was off and i was using the shift key.

"Page Down" with Num lock OFF correctly works as "Page Down".
"Page Down" with Num lock ON works as "SHIFT+Page Down" instead of "3".

I checked key bindings for both applications and can not find anything. And if i look at the registered hooks in the Sublime Text Console, it already registers with the Shift-Key pressed (with Num lock ON, Sublime Text 3 registers "Page Down" as "SHIFT+Page Down").

This **only **happens in the two aforementioned applications. In Firefox/Chromium/GEdit/Terminal/whatever it works just fine. I have checked the XFCE global keybindings and whatnot but can not find anything. The most confusing thing is that it works with all but those two applications.

Any ideas?

---

### Post by pere2 on 2016-01-14
Same issue.

Accessing via XRDP or VNC Wine KeyPad not working

Accessing v is XRDP or VNC Chrome, libre Office etc works ok

Acessing via VMWARE console everything weorks ok


Any idea please?

---

### Post by florian14 on 2016-02-18
> **pere2 said:**
> Same issue.

Accessing via XRDP or VNC Wine KeyPad not working

Accessing v is XRDP or VNC Chrome, libre Office etc works ok

Acessing via VMWARE console everything weorks ok


Any idea please?

Hah, that's the exact same thing.

Keypad via VMWARE works fine, keypad via X2GO works fine but with XRDP, the issue persists. This is so strange.

---

### Post by Tub3m4n on 2016-03-03
I'm having the exact same issue with Sublime Text 3 and also with PyCharm. Did anyone already find a solution to this problem?

---

### Post by Eva_Bouwman on 2016-03-05
I had the same issue, but fixed it. Maybe you already tried this I recently started using linux so I am a newby in helping other people

At desktop press alt+F2 enter system settings

at the hardware tab choose input devices

go to the third tab, mine is Dutch and called advanced (not sure if it is called the same in English)

there you can adjust the settings for numeric keypad you have to see what options are available according to your keyboard.

Hope it helps

---

### Post by Tub3m4n on 2016-03-08
I finally solved the problem by editing the keymap file. In my case this is km-0409.ini but it should work for all files.

Before you start, please create a backup of your keymap file as this is something that is not thoroughly tested and may interfere with other things.

1. In case you use another keymap file, run **xmodmap -pk > Layout.txt **from a terminal. In that file look for the key numbers associated with the *KP_ *keys. In my default file these are the key numbers between 79 and 91.
2. Go to /etc/xrdp and sudo edit the keymap file you are using (e.g. km-0409.ini) and replace the values of the keys you identified in the previous step with the correct unicode values ([http://unicode-table.com/en/#control-character](http://unicode-table.com/en/#control-character)). I only changed the values under [noshift]. For me the values were as follows:

Key number | New value | Character displayed
79 | 55:55 | 7
80 | 56:56 | 8
81 | 57:57 | 9
82 | 45:45 | -
83 | 52:52 | 4
84 | 53:53 | 5
85 | 54:54 | 6
86 | 43:43 | +
87 | 49:49 | 1
88 | 50:50 | 2
89 | 51:51 | 3
90 | 48:48 | 0
91 | 46:46 | .

3. Save the file and reboot the system. 

There is one small issue that I could not solve yet and that is the fact that the numbers now only work when Num Lock is off. In the remote session this is no problem as it seems that all other programs still show the correct input from the keypad even when Num Lock is off. When going back to the host system this is of course still a problem. Maybe this can be solved by also changing the values under the [shift],  [alt-gr], [capslock], ... items but I haven't had time to check that  yet.

**Edit: **Confirmed it works with Num Lock on when you change the values under all items in the ini file [shift], [noshift], [capslock], ... Again, this might break other stuff but for now it works.

**Edit2:** This will obviously break the non-Num Lock input so it becomes impossible to use e.g. the Home or PgUp key from the numeric keypad. This can most likely be solved by only changing values before or after the ':' and in some specific items in the ini file. As I don't use these keys on the numeric keypad this is no issue for me.

---

### Post by pere2 on 2016-04-21
Great!  All my  linux xrdp users are happy now!!!! Thank you very very much


changed in all the sections in my /etc/xrdp/km-0409.ini

Key79=55:55
Key80=56:56
Key81=57:57
Key82=45:45
Key83=52:52
Key84=53:53
Key85=54:54
Key86=43:43
Key87=49:49
Key88=50:50
Key89=51:51
Key90=48:48
Key91=46:46



Thnans again

---

