---
title: "Synaptic stopped upgrading and installing"
date: 2006-01-11
forum: Repositories &amp; Backports
---

### Post by DaveLinde on 2006-01-11
If there's something obvious... please point me.  Otherwise, some pointers on troubleshooting steps would be much appreciated.

I've got a pretty fresh install and I was able to take the first set of updates Synaptic found with no problems.  I downloaded half a dozen other programs with no problems.

Yesterday I clicked OK to take two updates and I got a message

[INDENT]Upgrade Finished
Failed to apply all changes! Scroll in the
terminal buffer to see what went wrong[/INDENT]

I opened the terminal which only says

[INDENT]Preconfiguring packages ...[/INDENT]

Now I can't add packages either - tried to get a copy of nvu and it bombed the same way.

Per something I read I did

```
apt-get install -f   
dpkg --configure -a
```

didn't change anything.

My situtation seems so simple I'd hoped I'd find someone else who hit and solved this already.  But on first looks, no one...  I'm hoping I did something dumb and am missing something obvious.  If not, I'll roll up my sleeves 'cause this new box won't be much fun if I can't load anything else to play with :( 

-Dave Lindemulder

---

### Post by 23meg on 2006-01-11
What error do you get when you try to install packages? Do these in order and see if it helps: remove all packages marked as "broken" in Synaptic, and then do

```
sudo apt-get -f install
sudo apt-get update

```

---

### Post by DaveLinde on 2006-01-12
[QUOTE=23meg]What error do you get when you try to install packages? [/QUOTE]

That's the problem... no errors beyond the failure seen from Synaptic.
apt-get install -f seems happy enough, now telling me that 11 updates are waiting.  apt-get update gets something and finishes happy too.

I guess I don't understand enough of what synaptic is doing (in what sequence) to do it from the command line and look for more error info to debug this.  Is there something I can tail? a verbose flag to set?  It's dying too quietly.

---

### Post by DaveLinde on 2006-01-17
ok...  googled a bit and dug inside this synaptic thing.  I have a list of 11 things to update and decided to try them one at a time manually.  First command was

```
sudo apt-get install apache2
```

and I got

```
Preconfiguring packages ...
dpkg: syntax error: unknown group `postdrop' in statusoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

so I poked around and found

```
dave@snoopy:/var/lib/dpkg$ cat statoverride
root postdrop 02555 /usr/sbin/postqueue
hplip root 755 /var/run/hplip
postfix postdrop 02710 /var/spool/postfix/public
root postdrop 02555 /usr/sbin/postdrop
```

it's a bit more descriptive,  ideas of where to go from here?  ...thanx.

---

### Post by DaveLinde on 2006-01-19
With a bit more searching I found several instances of this problem but no solution...  Based on the man page for dpkg-statoverride I got an idea.

If I read it correctly the statoverride file shows a change in permissions/ownership that are supposed to have been applied already.  It seemed that maybe something was supposed to create a new group, but didn't, and the statoverride was mistakenly updated.  Based on this logic I didn't see the harm in simply removing the lines that use the  missing group, making the new statoverride file:

```
hplip root 755 /var/run/hplip
```

Then instead of trying to install a package I ran

```
sudo apt-get upgrade
```

... well, it worked.  The 11 queued updates applied and now I can use synaptic to get other packages.  Now what?  Do I need to do some more manual repairs like creating a group and doing the override myself?

I'm happy things are working again but nervous I don't completely understand the cause of the failure or the impact of my hacking...

---

### Post by keller.baum on 2006-05-09
I've had the same problem and the same solution worked, mine occured after trying to install mysql and postfix.  I'd like to know what happened as well if anyone figures it out.

---

