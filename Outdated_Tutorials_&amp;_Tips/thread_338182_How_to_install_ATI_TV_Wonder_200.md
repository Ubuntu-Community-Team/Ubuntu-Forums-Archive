---
title: "How to install ATI TV Wonder 200"
date: 2007-01-14
forum: Outdated Tutorials &amp; Tips
---

### Post by phossal on 2007-01-14
The card should be plug-and-play in Edgy, but it isn't always recognized correctly.

[COLOR="SlateGray"]**STEP: **[/COLOR]Create the file *cx88xx* in the /etc/modprobe.d/ directory
```
cd /etc/modprobe.d/
sudo gedit cx88xx

```
[COLOR="SlateGray"]**STEP: **[/COLOR]Copy and paste the following. Save the file and close it.
```

options cx88xx card=4 tuner=44

```

[COLOR="SlateGray"]**STEP: **[/COLOR]Reload the module.
```

sudo modprobe -r cx8800
sudo modprobe cx8800

```

---

### Post by dvarsam on 2007-01-20
Hello!

[QUOTE=phossal]**[COLOR="#248"]Install ATI TV Wonder 200[/COLOR]**...[/quote]

Can you please add a snapshot of your product "**ATI TV Wonder 200**" on your original "HowTo" post?
It is always better to add a picture of the product you are talking about...

Thanks.

P.S.> If you don't know how to do this:

1. visit the site: [www.photobucket.com](www.photobucket.com)

2. Create an account inside that site.

3. Upload your product's picture in that site.
Note: If you don't have a picture of your product, you can search for one in the internet.

4. Under the list of all your uploaded pictures:

a. Click on the right of the box named "IMG Code" & the text named "[I M G]http://i69.photobucket.com/albums/i58/your_account_name/your_picture's_name.png[/I M G]" will be selected.

b. Perform a copy (on the selected text) & paste it inside your original post.

---

### Post by phossal on 2007-01-21
Posted link to ATI.

---

### Post by mikkelwe on 2007-04-29
> **phossal said:**
> The card should be plug-and-play in Edgy, but it isn't always recognized correctly.

[COLOR="SlateGray"]**STEP: **[/COLOR]Run the following commands one at a time:

```
cd /etc/modprobe.d/
sudo echo "options cx88xx card=4 tuner=44" > cx88xx
modprobe -r cx8800
modprobe cx8800

```

That won't work.
you need
sudo su -c 'echo "options cx88xx card=4 tuner=44" > cx88xx' or somthing or
echo "options cx88xx card=4 tuner=44" | sudo tee cx88xx

modprobe needs to be run with sudo as well.
or just sudo -i first to get a root prompt and type all the commands without sudo.

---

### Post by phossal on 2007-04-29
Sure, use sudo with modprobe. That's okay, too. The echo trick works, but it's more clear just to create the text file with an editor and *paste* the contents. tee works, too, but with the unnecessary addition of printing to stdout.

[edit] What brought you to this tutorial?

---

