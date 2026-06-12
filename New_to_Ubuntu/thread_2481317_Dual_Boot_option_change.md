---
title: "Dual Boot option change"
date: 2022-11-25
forum: New to Ubuntu
---

### Post by bewildered-newbie on 2022-11-25
I'm a recovering Windows 7 user who has just installed Mate alongside Win 7. Both OSes work as advertised but Win is preferred OS. What file(s) must be updated to change default OS from Ubuntu to Win 7  ? Since I am a "newbie" plz keep the answer simple & specific (which editor to use, etc).  Thanx.

Bewildered Bob

---

### Post by ajgreeny on 2022-11-25
You will have to edit the ***/etc/default/grub*** file.
To see what is in that file at this time show us the output of command ```
cat /etc/default/grub
``` and copy the output back here.

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**
I suspect you will need to change the line which will currently be ***GRUB_DEFAULT=0*** to ***GRUB_DEFAULT=2*** but wait until we've seen the file before making any changes.

---

### Post by tea for one on 2022-11-25
Windows 7 is now unsupported and does not receive security updates.
It reached End of Life more than 2 years ago (14 January 2020)
Therefore, it is sensible to use Ubuntu (22.04 hopefully) as your preferred OS.

---

### Post by ajgreeny on 2022-11-25
> **tea for one said:**
> Windows 7 is now unsupported and does not receive security updates.
It reached End of Life more than 2 years ago (14 January 2020)
Therefore, it is sensible to use Ubuntu (22.04 hopefully) as your preferred OS.
A very good point, and one I ought to have mentioned, though I assumed you were well aware of this situation., which is why you installed Ubuntu

Nevertheless you really must not go online any more when using Windows 7 because it will be at huge risk as a result of those almost 3 years of no security updates.

---

### Post by tea for one on 2022-11-25
> **ajgreeny said:**
> Nevertheless you really must not go online any more when using Windows 7 because it will be at huge risk as a result of those almost 3 years of no security updates.
Yes, completely, absolutely and fundamentally.
It is quite remarkable the number of incidences of Windows 7 in these forum pages.
Especially, when Windows 10 was a free upgrade?

---

### Post by bewildered-newbie on 2022-11-26
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

# How did I do ?

---

### Post by bewildered-newbie on 2022-11-26
Thanx for the very reasonable recommendation to abandon Win 7 due to lack of security updates. But MS does issue regular updates for "MS Security Essentials" which when combined with Malwarebytes Anti-Virus has apparently protected me since the end-of-life. Am I just lucky ??  Thanx.

Bewildered Bob

---

### Post by tea for one on 2022-11-26
> **bewildered-newbie said:**
>  Am I just lucky ?
Yes, you are.
The last release of MS Security Essentials is dated 10 November 2021.
[https://downloads.digitaltrends.com/microsoft-security-essentials/windows](https://downloads.digitaltrends.com/microsoft-security-essentials/windows)

---

### Post by ActionParsnip on 2022-11-26
Easy to rearrange grub. The number of the file dictates where it appears in the list
```

sudo mv /etc/grub.d/30_os-prober /etc/grub.d/08_os-prober

sudo update-grub

```

Reboot to test. As stated above Windows 7 is end of life and not considered secure. It shouldn't be used by anything accessing the Internet.

---

### Post by yancek on 2022-11-27
> GRUB_DEFAULT=0

Edit the line above in the /etc/default/grub file with your favorite text editor using root privileges (sudo) and replace the zero with the number of the windows entry you want.  Grub counts from zero.  Save the change and update grub.

---

### Post by bewildered-newbie on 2022-11-27
> **yancek said:**
> Edit the line above in the /etc/default/grub file with your favorite text editor using root privileges (sudo) and replace the zero with the number of the windows entry you want.  Grub counts from zero.  Save the change and update grub.

Thanx for the quick reply but since I'm a "newbie" there is no "favorite text editor" (yet).  Which one(s) is recommended ?  Which software option is easiest to use to download & install ?


Bewildered Bob (running Mate 20.04)

---

### Post by ajgreeny on 2022-11-27
Mate which you are using already has a text-editor installed, ie, pluma, so look for that or use command ```
sudo -H pluma /etc/default/grub
``` which will open that file with root permissions.

I don't know if you have ever used nano, a terminal command-line text editor, but many experts would recommend that you use that for editing system-files, which you can do by default with command in this case with ```
sudoedit /etc/default/grub
``` so you may like to try that.  In the past using sudo with GUI applications could cause big problems with files in your home becoming owned by root and thus locking you out from your owner login.
That should no longer happen but I can't remember when the change happened; I think it was in 20.04 so you should be safe to use plain simple ***sudo pluma***, though the added ***sudo -H pluma*** that I show above adds an extra safety margin.

---

### Post by maglin2 on 2022-11-27
Has it been definitely established what number he wants for windows yet - presumably from grub.cfg?
2 seems likely, but... Maybe I missed it.

---

### Post by yancek on 2022-11-28
>  Has it been definitely established what number he wants for windows yet - presumably from grub.cfg?

No, but s/he has been told how to find it and how to change it in previous posts.  Just watching the entries on boot or going through grub.cfg would do it.

---

### Post by bewildered-newbie on 2022-11-28
The desired default is fifth one so I assume **DEFAULT=4** is correct.  Thanx for your help.

---

### Post by yancek on 2022-11-28
> The desired default is fifth one so I assume **DEFAULT=4** is correct 

That would be correct.  Make sure to save the change and run:  sudo update-grub

---

