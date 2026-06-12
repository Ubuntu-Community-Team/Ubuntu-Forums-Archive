---
title: "X-sensing in a bash script?"
date: 2010-04-10
forum: Programming Talk
---

### Post by NFblaze on 2010-04-10
So right now I have a script made that backs up my Tomboy Notes to a local zip file (since UbuntuOne is fidgety), when I run it. It's all fine and dandy in its current usage on my laptop. It also has a password, that is acquired via a zenity dialog box.

Now, there are times when Im out and about I think of a great brainstorm or idea. I SSH into my computer and can manually edit the XML file where Tomboy Notes stores it's data, but if I run the script it fails to execute properly because I dont have an GDM( or is it xserver?) session running.

What's the best way for me to incorporate into the script to prevent this from happening. I have a couple of ideas but would like to ask some more experienced scripters/programmers. Thanks

---

### Post by geirha on 2010-04-10
ssh in with the -X option to enable X11forwarding. GUI applications you run through the ssh session will then connect to the XServer running on your local computer.

```
ssh -X user@host 'zenity --info --text="test"'

```

You could also change your script to handle cases where an xserver is not available, by using something like dialog or whiptail instead of zenity.

```
if [[ $DISPLAY ]]; then
  echo "Xserver is available"
  zenity etc...
else
  echo "Xserver is not available"
  whiptail etc ...
fi

```

---

### Post by NFblaze on 2010-04-10
I usually SSH into my computer from my phone using ConnectBot or MidPSSH or if I'm at a computer that isnt mine I used PuTTY, which I dont think any of those runs an X-session.

I think the second method to failsafe into a different option like a read commandline would probrably work, tho. That's a rather insightful answer. Thanks

---

