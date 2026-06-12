---
title: "Menu in SH script"
date: 2009-01-02
forum: Programming Talk
---

### Post by Nott32 on 2009-01-02
hi,
Im working on a script I have all the code done now I want to make a menu for it but am having problems. 

can someone post a example that I can place my code into all the ones I find are outdated and wont run for different errors.


thanks :)

---

### Post by dwhitney67 on 2009-01-02
If all you need is a menu, then use a series of 'echo' statements to present the menu, and then use a 'read' to gather the operator's input.

For example:
```

#!/bin/sh

choice=""

while [ "$choice" != "q" ]
do
        echo
        echo "Please make a selection!"
        echo "1) Potato Soup"
        echo "2) Chopped Liver"
        echo "3) Whirled Peas"
        echo "4) Blazin' Hot Wings"
        echo "q) Quit"
        echo

        read choice

        case $choice in
            '1') echo "item 1 selected...";;
            '2') echo "item 2 selected...";;
            '3') echo "item 3 selected...";;
            '4') echo "item 4 selected...";;
            'q') echo "quiting!";;
            *)   echo "menu item is not available; try again!";;
        esac
done

exit 0

```

---

### Post by ghostdog74 on 2009-01-02
check out the bash script guide in my sig example 10.29. It uses "select" to create menus.

---

### Post by Nott32 on 2009-01-03
I used an example like this earlier but it outputs nothing

arcuser@ArcNix:~$ sh goarc3.sh
arcuser@ArcNix:~$ 


> #!/bin/sh

choice=""

while [ "$choice" != "q" ]
do
        echo
        echo "1) SVN Checkout"
        echo "1) Potato Soup"
        echo "2) Chopped Liver"
        echo "3) Whirled Peas"
        echo "4) Blazin' Hot Wings"
        echo "q) Quit"
        echo

        read choice

        case $choice in
            '1') cd /home/arcuser/installer/arcemu/ && svn co [http://www.arcemu.info/svn/;;](http://www.arcemu.info/svn/;;)
            '2') echo "item 2 selected...";;
            '3') echo "item 3 selected...";;
            '4') echo "item 4 selected...";;
            'q') echo "quiting!";;
            *)   echo "menu item is not available; try again!";;
        esac
done

exit 0

I hate being new to this :p

---

### Post by dwhitney67 on 2009-01-03
Your script runs fine for me.  The menu was displayed, the read succeeded, as well as the case/esac block.

---

### Post by Nott32 on 2009-01-03
Its working, I have to manually make the file using nano in SSH and copy past from my text editor. Thank you :)

---

