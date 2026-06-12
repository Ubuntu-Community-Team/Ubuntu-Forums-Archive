---
title: "HOWTO: Change Hellanzb Default Colors"
date: 2007-08-09
forum: Outdated Tutorials &amp; Tips
---

### Post by felicity on 2007-08-09
This tutorial is based on hellanzb 0.13 and Ubuntu 7.04 Feisty 32, though it should work with other Linux variations.  

If you use Hellanzb, you'll notice that some of the text output is colored differently than your default terminal font color. How then do we change these, arguably not very pretty, colors?

[COLOR="Navy"]Step 1: First let's enter the directory where the file resides:[/COLOR]
```
cd /usr/share/python-support/hellanzb/Hellanzb/
```

[COLOR="Navy"]Step 2: To save us future problems we should make a backup of the file we're going to edit in case something goes wrong:[/COLOR]
```
sudo cp Logging.py Logging.py.BACKUP
```

[COLOR="Navy"]Step 3: Great, now we're ready to edit the file:[/COLOR]
```
sudo gedit Logging.py
```

[COLOR="Navy"]Step 4: We need to scroll down until we find this section of the file:[/COLOR]

        [COLOR="DarkRed"]'F_DRED': '31'.
        'F_LRED': '31;1',
        'F_DGREEN': '32',
        'F_LGREEN': '32;1',
        'F_BROWN': '33',
        'F_YELLOW': '33;1',
        'F_DBLUE': '34',
        'F_LBLUE': '34;1',
        'F_DMAGENTA': '35',
        'F_LMAGENTA': '35;1',
        'F_DCYAN': '36',
        'F_LCYAN': '36;1',
        'F_WHITE': '37',
        'F_BWHITE': '37;1',
        }[/COLOR]

[COLOR="Navy"]Step 5: How to edit the colors:[/COLOR]

To edit the default colors we need to change the ANSI color codes (the numbers), NOT the words. But we can use the words as a map of which colors we are changing. 

For instance, in hellanzb the default color of the ETA time is yellow, so we know that if we change the color code next to the YELLOW variable we will be changing the color of the ETA time in hellanzb. This is explained in further detail below.

Here's a color chart we can use to determine the color code numbers:

[[img]http://www.Photo-Host.org/thumb/380261colors.png[/img]]("http://www.Photo-Host.org/view/380261colors.png")

We can see on the chart that Yellow is a bold version of Orange which is 33, so Yellow is 33;1 (bold colors have ;1 after them). Sure enough, that's what the file we're editing shows:
```
'F_YELLOW': '33;1',
```
So if we want to change the yellow ETA time to light (bright) green we would change the 33;1 to 32;1:
```
'F_YELLOW': '32;1',
```
Or, if we wanted to change the ETA time to Dark Blue we would use code 34:
```
'F_YELLOW': '34',
```

[COLOR="DarkGreen"]List of main variables and what text output they govern:[/COLOR]

[COLOR="DarkGreen"]F_YELLOW:[/COLOR] the ETA time
[COLOR="DarkGreen"]F_DRED:[/COLOR] download speed and KB/s
[COLOR="DarkGreen"]F_DGREEN:[/COLOR] percent remaining and megabytes remaining
[COLOR="DarkGreen"]F_DBLUE:[/COLOR] the brackets, @ symbol, and the server id, defined in /etc/hellanzb.conf > (defineServer(id = 'changeme')


[COLOR="Navy"]To restore your original file if something goes wrong, follow Step 1 above, then use this line:[/COLOR] 
```
sudo cp Logging.py.BACKUP Logging.py
```

If this tutorial needs any corrections please let me know, and enjoy your new colored hellanzb. ):P

---

### Post by dfm21 on 2007-08-10
Be sure to check out [HellaHella]("http://www.hellanzb.com/trac/hellanzb/wiki/HellaHella")!
It's a handy web frontend for hellanzb.

My setup: Edgy server, hellanzb with hellahella and a (Samba) shared folder, so I can drop nzbs from any PC in our LAN in one directory and control everything easily by browsing to [http://srv:5000](http://srv:5000). NICE!! :)

---

### Post by frolle on 2007-08-19
Hellaworld is even more nice and with firefox extension its great :)

---

