---
title: "How do I install Bittyrant on Linux?"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by Lesouteneur on 2008-06-01
What should I do to install Bittyrant on Ubuntu 8.04?

All I could manage to do is install Azureus without Bittyrant.

---

### Post by Joeb454 on 2008-06-01
Perhaps this link will help

[http://azureus.sourceforge.net/howto_linux.php](http://azureus.sourceforge.net/howto_linux.php)

You should note that it's install instructions for 32-bit systems (which you'll likely be running)

---

### Post by philinux on 2008-06-01
Seeing as all the software is free give Deluge a go.

It's in synaptic or from their website.

---

### Post by shifty_powers on 2008-06-01
actually really like deluge. utorrent via wine is good too ;)

---

### Post by Lesouteneur on 2008-06-01
> **philinux said:**
> Seeing as all the software is free give Deluge a go.

It's in synaptic or from their website.

I have. But it is slow compared to Bittyrant or regular Azureus.

---

### Post by Joeb454 on 2008-06-01
Did you try the instructions I posted above?

---

### Post by Lesouteneur on 2008-06-01
> **Joeb454 said:**
> Did you try the instructions I posted above?

Yes. Great! I got it to run. Theres one problem though.When it gets to step [HTML]3) Change to the azureus directory and run ./azureus to start

    * cd azureus
    * ./azureus[/HTML]

It doesn't work. the terminal says.

[HTML]framirez@ramirez-desktop:~$ cd azureus
framirez@ramirez-desktop:~/azureus$ ./azureus
bash: ./azureus: Permission denied
[/HTML]


So then I did what it says. to run it manually

[HTML]java -cp swt.jar:swt-pi.jar:Azureus2.jar -Djava.library.path=./ org.gudy.azureus2.ui.swt.Main[/HTML]

But How do I make it so an icon shows up?

---

### Post by Xiong Chiamiov on 2008-06-01
I'm not too familiar with jars, but usually if you get a permission denied error on an executable, you need to give it permission to execute:
```

chmod +x [filename]

```

---

### Post by Lesouteneur on 2008-06-01
> **Xiong Chiamiov said:**
> I'm not too familiar with jars, but usually if you get a permission denied error on an executable, you need to give it permission to execute:
```

chmod +x [filename]

```

Nothing happened.This is what I get:

[HTML]framirez@ramirez-desktop:~/azureus$ chmod +x ./azureus
framirez@ramirez-desktop:~/azureus$ 

[/HTML]

---

### Post by Joeb454 on 2008-06-01
Now run ```
./azureus
``` again :)

---

### Post by Lesouteneur on 2008-06-01
> **Joeb454 said:**
> Now run ```
./azureus
``` again :)

Thank you. You were very helpful. I got the launcher to work too. I just picked the azureus.sh file as a command under the add menu.

---

