---
title: "Change Date/Time Formats"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by iaskedalice09 on 2008-08-04
Hi again!

Installed Ubuntu successfully. Now for another question!

How do you get the date format t be DD-MMMM-YYYY e.g., 4 Aug 08, and the time to be 24 hour, like 19:46?

I saw a post but I could figure out what to do in Terminal.

---

### Post by sharks on 2008-08-04
just right click the time, select preferences and change it to 24 hour format.

---

### Post by iaskedalice09 on 2008-08-04
> **sharks said:**
> just right click the time, select preferences and change it to 24 hour format.

Thanks so much! It works! Now for the date, what do I do?

---

### Post by sharks on 2008-08-04
take a look:
[www.ubuntuforums.org/showthread.php?t=193916](www.ubuntuforums.org/showthread.php?t=193916)

---

### Post by iaskedalice09 on 2008-08-04
I couldn't get it to edit with Terminal and didn't save int the Text Editor. What do I do?

---

### Post by sharks on 2008-08-04
does it say permission denied when saving?

---

### Post by iaskedalice09 on 2008-08-04
Yes.

---

### Post by iaskedalice09 on 2008-08-04
Should I CHMOD the file to 775 or something temporarily?

---

### Post by iaskedalice09 on 2008-08-04
K, I changed the owner to me, editted the file, and changed it back to root.

The code I change the appropriate date format to was this:

```

% Appropriate date representation (%x)
%	"%d-%m-%Y"
d_fmt   "<U0025><U0063><U007E><U0025><U006D><U007E><U0025><U0059>"
%

```

That is for DD-MMM-YYYY. And it works, and I didn't have to log out/in.

To change ownership, in Terminal, type:
```

sudo chown username:username /path/to/file/

```
So, say the owner's username is Jane. She wants to change the file "en_US" to belong to her. She would type in Terminal
```

sudo chown jane:jane /usr/share/locales/en_US/

```
and to change it back to root, she types
```

sudo chown root:root /usr/share/locales/en_US/

```
I'm sure the person helping me knows all of the stuff I'm talking about, but in case someone runs across this via google or something.

---

### Post by kaibob on 2008-08-05
The OP wanted something comprehensive, but for those only wanting to customize the date/time format of the Clock applet, this can be done by changing two keys in gconf-editor. The first key should be changed to custom:

/apps/panel/applets/applet_1/prefs/format

The second key should be changed to the desired date/time format:

/apps/panel/applets/applet_1/prefs/custom_format

It should be noted that:

* The above applies to Hardy only.

* The word, applet_1, in the second key noted above may have a different number. 

A page that provides helpful information on date/time formats is:

[http://us.php.net/strftime](http://us.php.net/strftime)

Source Reference:
[http://ubuntuforums.org/showthread.php?t=780676](http://ubuntuforums.org/showthread.php?t=780676)

---

### Post by iaskedalice09 on 2008-08-06
I forgot how to change to the 24-hour-clock in en_US. While his solution worked for the official system clock, it didn't work for applications like Thunderbird. Here's my code:

```

% Appropriate time representation (%X)
%	"%R"
t_fmt   "<U0025><U0052>"
%
% Appropriate AM/PM time representation (%R)
%	"%H:%M:%S %p"
t_fmt_ampm "<U0025><U0049><U003A><U0025><U004D><U003A><U0025><U0053><U0020>/
<U0025><U0070>"
%
% Strings for AM/PM
%
am_pm	"<U0041><U004D>";"<U0050><U004D>"
%

```

Don't take out the AM/PM parts because those just screwed it up for me, and 20:15 comes out 20:15 and not 20:15 PM even though the AM/PM parts are still in there. :)

---

### Post by iaskedalice09 on 2009-04-26
Alternatively, you can go to System > Administration > Language Support and change it there.

---

