---
title: "running .sh files"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by Cossar on 2008-08-16
Hey there. I just got to my dorm room, and to access the internet I have to log in with my account. I log in through the browser, and a "Bradford_Dissolvable_agent.sh" pops up for download. Once downloaded, I tried running it with the autorun prompt but it would just show that it was busy and nothing would pop up. how would I get the .sh file to run? I'm using Firefox and ubuntu 8.04 if that's any help.
Thanks

---

### Post by Flyingjester on 2008-08-16
have you tried running it in terminal?

---

### Post by sharks on 2008-08-16
i think it is > sh nameofthefile.sh

---

### Post by NovaAesa on 2008-08-16
You need to set the file to being executable. Right click on it then go to properties -> permissions and check the executable check box (or you could use chmod, but that's the h4xx0r way). Now go to the terminal and cd to the file. Then run:
```

./nameofthefile.sh

```

---

### Post by Cossar on 2008-08-16
I just tried it in terminal but I get "sh: Can't Open nameoffile.sh"

---

### Post by Bachstelze on 2008-08-16
> **Cossar said:**
> I just tried it in terminal but I get "sh: Can't Open nameoffile.sh"

What did you try, exactly?

---

### Post by sharks on 2008-08-16
first go to the directory
cd /theplace/where-u-have-the-file
sh nameofthefile.sh 

or 
./nameofthefile.sh

---

### Post by Cossar on 2008-08-16
ah, thanks, I clicked that and ran it in terminal and I got this:> mkdir: cannot create directory `.CSA.TEMP': File existsawk: cmd. line:1: fatal: cannot open file `/home/cossar/Desktop//home/cossar/Desktop/Bradford_Dissolvable_Agent(2).sh' for reading (No such file or directory)tail: +: invalid number of linesgzip: stdin: unexpected end of filetar: This does not look like a tar archivetar: Error exit delayed from previous errorschmod: cannot access `./engine': No such file or directory/home/cossar/Desktop/Bradford_Dissolvable_Agent(2).sh: 11: ./engine: not found/home/cossar/Desktop/Bradford_Dissolvable_Agent(2).sh: 12: function: not found/home/cossar/Desktop/Bradford_Dissolvable_Agent(2).sh: 18: mozilla: not found/home/cossar/Desktop/Bradford_Dissolvable_Agent(2).sh: 18: mozilla: not found/home/cossar/Desktop/Bradford_Dissolvable_Agent(2).sh: 19: function: not found/home/cossar/Desktop/Bradford_Dissolvable_Agent(2).sh: 25: netscape: not found/home/cossar/Desktop/Bradford_Dissolvable_Agent(2).sh: 25: netscape: not found/home/cossar/Desktop/Bradford_Dissolvable_Agent(2).sh: 26: function: not found/home/cossar/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored./home/cossar/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored./home/cossar/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

and an error message pops up in the browser referring to this: file://localhost/home/cossar/Desktop/.CSA.TEMP/results.html

---

### Post by Flyingjester on 2008-08-16
looks like you typed it in wrong.

---

### Post by ingeva on 2008-08-16
> **Flyingjester said:**
> looks like you typed it in wrong.

Could it be an idea to post the file here -- if it's long, then as an attachment?

Otherwise, I usually set the execute bit by using chmod +x filename,
and if it's a shell command file I use bash filename.

---

