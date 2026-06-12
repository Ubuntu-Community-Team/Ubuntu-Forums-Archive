---
title: "Sed cannot remove line ending in a pattern"
date: 2014-10-03
forum: Programming Talk
---

### Post by TitoHL on 2014-10-03
Hi guys:
I am learning to create scripts, but I've had troubles with SED command. In particular, when I try delete a line that ends with a pattern.
My example is, boot.txt, a text file that contains three lines:
```

[      16518 2014-09-23 16:09]  /boot/grub/grub.cfg
[       1024 2014-10-02 14:49]  /boot/grub/grubenv
[COLOR=#333333][       1024 2014-10-02 14:49]  /boot/grub/grubenvx[/COLOR]
```
According to the documentation, to remove only the 2nd line (ends with grubenv), I would use the following command:
```
[COLOR=#333333]sed -e '/grubenv$/d' boot.txt > boot2.txt[/COLOR]
```
Theoretically, the result should be that boot2.txt containing:
```

[      16518 2014-09-23 16:09]  /boot/grub/grub.cfg
[COLOR=#333333][       1024 2014-10-02 14:49]  /boot/grub/grubenvx[/COLOR]
```
However, the result is that the content of boot2.txt remains the same boot.txt.
What am I doing wrong? 
In advance, thank you very much. 
PS: I know you can use other commands to do this, but my intention is to learn to use either the SED command.

---

### Post by matt_symes on 2014-10-03
Hi

I can see much wrong.

```

matthew-laptop:/home/matthew:0 % ls test*
test
matthew-laptop:/home/matthew:0 % cat test 
[      16518 2014-09-23 16:09]  /boot/grub/grub.cfg
[       1024 2014-10-02 14:49]  /boot/grub/grubenv
[       1024 2014-10-02 14:49]  /boot/grub/grubenvx
matthew-laptop:/home/matthew:0 % sed -e '/grubenv$/d' test > test2       
matthew-laptop:/home/matthew:0 % ls test*
test  test2
matthew-laptop:/home/matthew:0 % cat test2
[      16518 2014-09-23 16:09]  /boot/grub/grub.cfg
[       1024 2014-10-02 14:49]  /boot/grub/grubenvx
matthew-laptop:/home/matthew:0 % 

```

The only thing i have changed are the filenames. Linux filenames don't usually require extensions. Maybe i should strike out that last comment in the programming sub-forum :)

You are running the commands on a Ubuntu box ? The file boot.txt was created on a Ubuntu box ?

Kind regards

---

### Post by ofnuts on 2014-10-03
I don't think file extensions are the problem, but some overlooked space character between grubenv and the EOL would cause the problem.
```

sed -e '/grubenv\s*$/d' boot.txt

```
would take care of any number of feral spaces/tabs at the end of the line.

---

### Post by TitoHL on 2014-10-03
Ofnuts, you hit the bulls-eye!
Trouble solved.
Thank you very much.
Too, thanks Mattew for try to helpme.
Greetings from Chile.

---

### Post by matt_symes on 2014-10-03
Hi

> **ofnuts said:**
> I don't think file extensions are the problem.

LOL. Yeah. That's not what i meant by that comment.

But anyway, good catch there sir. :)

Kind regards

---

