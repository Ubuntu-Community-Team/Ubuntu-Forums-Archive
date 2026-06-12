---
title: "How to open a .sh script - automatically in bash using metacity?"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by J05HYYY on 2008-05-14
I know it's a bit windowsy, but is there a way of double clicking on a file with the ".sh" extension and then opening it in a new instance of the terminal?

Don't know how to do it ... couldn't find out how to do it. :S

---

### Post by Het Irv on 2008-05-14
If the file is set up to run as a exicuteable, I should ask you what you want to do with it, one of the options is run in terminal.

---

### Post by kosmic on 2008-05-14
In linux everything is a file, so you can open anything in a text pad ;)

if you tell linux that the .sh program is in really an executable (chmod +x) then if you double click that file linux will try to execute the script.

To open the file just remove the executable flag (chmod -x) or else when you double click the file choose the opion "DISPLAY" to see the file.

---

