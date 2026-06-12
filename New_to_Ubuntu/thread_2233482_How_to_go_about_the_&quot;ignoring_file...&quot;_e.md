---
title: "How to go about the &quot;ignoring file...&quot; error when I update in the terminal"
date: 2014-07-08
forum: New to Ubuntu
---

### Post by badgethefarmer on 2014-07-08
Looks like this:

```
N: Ignoring file 'canonical_partner.list’' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'canonical_partner.list’' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

```

---

### Post by oldos2er on 2014-07-08
Is there an [s]comma[/s] apostrophe on the end of canonical_partner.list ? ```
ls /etc/apt/sources.list.d/canonical_partner*
```

---

### Post by badgethefarmer on 2014-07-08
I believe there is none?

```
/etc/apt/sources.list.d/canonical_partner.list
/etc/apt/sources.list.d/canonical_partner.list’
/etc/apt/sources.list.d/canonical_partner.list.save

```

---

### Post by Bucky Ball on 2014-07-08
> **badgethefarmer said:**
> ```

/etc/apt/sources.list.d/canonical_partner.list&#8217;


```

This may be the line olddos2er is talking about. See the apostrophe at the end (rather than a comma)? Open a terminal and comment out that line using a hash (#) at the beginning:

```
# sudo nano /etc/apt/sources.list'
```

Control+x, 'y' and try again (sudo apt-get update).

---

### Post by oldos2er on 2014-07-08
> **badgethefarmer said:**
> I believe there is none?

```
/etc/apt/sources.list.d/canonical_partner.list
[COLOR=#ff0000]/etc/apt/sources.list.d/canonical_partner.list&#8217;[/COLOR]
/etc/apt/sources.list.d/canonical_partner.list.save

```

Except there is, as Bucky noted.

Edit: I really do know the difference between a comma and an apostrophe. Fixed previous post.

---

### Post by badgethefarmer on 2014-07-09
> **Bucky Ball said:**
> This may be the line olddos2er is talking about. See the apostrophe at the end (rather than a comma)? Open a terminal and comment out that line using a hash (#) at the beginning:

```
# sudo nano /etc/apt/sources.list'
```

Control+x, 'y' and try again (sudo apt-get update).

Hello there. 

I did enter the code ```
# sudo nano /etc/apt/sources.list'
``` you showed here then did the sudo update. But I still get this at the end of the update ```
N: Ignoring file 'canonical_partner.list’' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

```

I wonder what I did wrong. I was trying to install Skype as Skype isnt readily available in the Ubuntu Center. So I was following some ways to install skype via the terminal and was instructed to add codes or like to add repositories to get the skype to download and install. Then afterwards, whenever I sudo update, I get that error code at the end.

Sorry, I just want to understand how this works. :) I just don't want a fix but I want to know the reason why this happens and what I did for this to happen.

Thanks :)

---

### Post by Bucky Ball on 2014-07-09
A/ Skype is available from the repositories, no need to install manually, and if it's not, something is odd;
B/ Did you make that change in the *sources.list* file and not in a terminal? Could you post here the section you changed, please?

This:

```
N: Ignoring file 'canonical_partner.list’' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
```

... tells us that line is not being ignored by using a hash or removal. You need to do this:

```
sudo nano /etc/apt/sources.list
```

... and find the line that ends with the apostrophe: canonical_partner.list’. Stick a hash at the beginning of that line. 

Hit control + x, then 'y' and update.

PS: sources.list.d is a directory, not a file, so there might lay the confusion. To see if there is something in there that shouldn't be:

```
dir /etc/apt/sources.list.d
```

... and let's see what's there.

---

### Post by badgethefarmer on 2014-07-09
Can I just delete that file in the Nautilus file manager?

---

### Post by Bucky Ball on 2014-07-09
Might not have permissions to do so.

Do this:

```
dir /etc/apt/sources.list.d
```

Do you see the file there?

```
sudo rm canonical_partner.list&#8217;
```

Two commands, that easy. ;)

---

### Post by badgethefarmer on 2014-07-09
What result should i see after doing sudo rm on that file I want to remove?

Currently, there is just a blinking cursor.

---

### Post by deadflowr on 2014-07-09
> **badgethefarmer said:**
> What result should i see after doing sudo rm on that file I want to remove?

Currently, there is just a blinking cursor.

That should be it.
You could rerun the ls command to see if it is still listed.
Then, of course, try rerunning the update command again.

I'm oblivious to other flavors and how they work, but I thought that the canonical partners was part of the default sources.list file.
You simply needed to uncomment it.
Don't know it Xubuntu, but the line is in the sources.list for Kubuntu.

Quick edit:

My bad, you might need to though the file name around some quotes.
```
sudo rm canonical_partner.list’
```
to
```
sudo rm "canonical_partner.list’"
```
notice I added the double quotes/unquotes

If it is hanging, ctrl +C to cancel, ftr.

---

### Post by Bucky Ball on 2014-07-09
You shouldn't see anything. Just removes. Close that terminal and:

```
cd /etc/apt/sources.list.d
dir
```

Do you see the file there? if you do:

```
sudo rm canonical_partner.list&#8217;
```

I'm a bit stumped as to how it ended up in sources.list.d. :-k

deadflowr: We ninja-ed! Sorry about that. ;)

---

### Post by hbutt875 on 2014-07-09
Hello go to ubuntu software center>edit>last option (software source)
Now go to other software tab.
unselect canonical partners>enter password and click ok
Now try the update and reply it works or not.

---

### Post by deadflowr on 2014-07-09
> I'm a bit stumped as to how it ended up in sources.list.d. :-k

Me, too.
Could it be an error on a save.
Like when you save with nano and it asked to overwrite and then the file name(which most of the time users take as is., which you can change, All it would take is a fat finger error.

---

### Post by Bucky Ball on 2014-07-09
> **hbutt875 said:**
> Hello go to ubuntu software center>edit>last option (software source)
Now go to other software tab.
unselect canonical partners>enter password and click ok
Now try the update and reply it works or not.

Not this. It quite possibly won't fix the issue as it appears to be a stray file in sources.list.d with an apostrophe on the end that is the culprit. There seems to be nothing with any repositories. ;)

> **deadflowr said:**
> Me, too.
Could it be an error on a save.
Like when you save with nano and it asked to overwrite and then the file name(which most of the time users take as is., which you can change, All it would take is a fat finger error.

Hmm. True.

---

### Post by badgethefarmer on 2014-07-09
Upon typing these codes, this one comes up

```
rm: cannot remove &#8216;canonical_partner.list'&#8217;: No such file or directory
```

---

### Post by deadflowr on 2014-07-09
Run the ls command again.
```
ls /etc/apt/sources.list.d
```

---

### Post by badgethefarmer on 2014-07-10
```
/etc/apt/sources.list.d/canonical_partner.list
/etc/apt/sources.list.d/canonical_partner.list’
/etc/apt/sources.list.d/canonical_partner.list.save
```

---

### Post by Bucky Ball on 2014-07-10
Once again:

```
cd /etc/apt/sources.list.d
sudo rm canonical.partner.list'
```

Copy and paste those two commands one at a time into a terminal and hit return after each. Then you're done. Then:

```
sudo apt-get update
```

Any errors? If so, paste them exactly here, please.

---

### Post by oldos2er on 2014-07-10
Perhaps try ```
sudo rm "canonical.partner.list'"
``` the apostrophe might be confusing the shell.

---

### Post by deadflowr on 2014-07-10
> **oldos2er said:**
> Perhaps try ```
sudo rm "canonical.partner.list'"
``` the apostrophe might be confusing the shell.

My thought exactly.
Or Perhaps try enclosing the whole path in quotes
```
sudo rm "/etc/apt/sources.list.d/canonical_partner.list'"
```

---

### Post by Bucky Ball on 2014-07-10
> **oldos2er said:**
> Perhaps try ```
sudo rm "canonical.partner.list'"
``` the apostrophe might be confusing the shell.

+1. Thanks.

---

