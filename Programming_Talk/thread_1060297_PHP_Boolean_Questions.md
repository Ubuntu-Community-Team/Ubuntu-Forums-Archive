---
title: "PHP Boolean Questions"
date: 2009-02-04
forum: Programming Talk
---

### Post by cerealtx on 2009-02-04
i created a php program that searches a site, finds videos, downloades them, and then using HandBrakeCLI im converting them for my ipod, could i setup a contional like 
```
if($convertvid = shell_exec("./HandBrakeCLI -i $vidipath$results[1] -o $vidopath$results[1].mp4 --preset=\"iPhone & iPod Touch\"")
{
yah it converted, go on
}
else
{
did not convernt, do this
}
```
is that going to return me a 0 or a 1 for boolean purpouses??

---

### Post by drubin on 2009-02-04
> **cerealtx said:**
> 
is that going to return me a 0 or a 1 for boolean purpouses??

No shell_exec return what ever the command out putted to the output stream.

if you are wanting to return the exit code (ie was the command successful or not) you need the extram params passed to the function

take a look here [http://www.php.net/manual/en/function.exec.php](http://www.php.net/manual/en/function.exec.php)

change your code to something similar to this. (not tested)
[PHP]shell_exec("./HandBrakeCLI -i $vidipath$results[1] -o $vidopath$results[1].mp4 --preset=\"iPhone & iPod Touch\"",$output,$status);
if($status == true)
{
echo "yah it converted, go on"; //Fixed this
}
else
{
echo "did not convernt, do this";  //fixed this
}[/PHP]

---

### Post by cerealtx on 2009-02-04
awesome thank you!

---

### Post by drubin on 2009-02-05
> **cerealtx said:**
> awesome thank you!

Great I assumed it worked?

---

### Post by cerealtx on 2009-02-05
yah man worked like a charm! but the best part was from that simple post i learned alot about regex well, it helped me peice alot of things together! much thanks man

---

### Post by drubin on 2009-02-05
> **cerealtx said:**
> yah man worked like a charm! but the best part was from that simple post i learned alot about regex well, it helped me peice alot of things together! much thanks man

Rather surprised it worked that is why i asked. hehehe  (Was typed late I was half sleeping).

Glad you learnt. Take a look at the php.net site for other functions they have little tutorials on how to use them with some basic demos you can learn tones.

---

