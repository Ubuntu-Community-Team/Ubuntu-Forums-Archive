---
title: "Network manager autoconnects.How to stop this?."
date: 2008-11-11
forum: New to Ubuntu
---

### Post by robert shearer on 2008-11-11
Just installed Intrepid and each time I boot up my wired eth0 autoconnects.

With Hardy it remembered it's status when the compy was powered down and on reboot it defaulted to that.

Example..if I right clicked on the network manager applet and unchecked "enable networking" then powered down, on reboot the applet would show the connection disabled until I right clicked and selected "enable networking"

With Intrepid, no matter what I select before shutdown it always autoconnects on reboot.

How can I take back control?? :)

---

### Post by bscbrit on 2008-11-11
The logic (and software) behind NetworkManager is different under Intrepid but what you are seeing is, if I've read the documentation properly, the 'correct' behaviour for the current version.  It also fails to handle static IPs and there are other issues as well.

While I accept that this is less than optimum I would recommend that you do 3 things.

1.  Raise a bug report so that the devs know that NM doesn't do what you, the user, want it to do.  It doesn't matter what someone else says it should do, if it doesn't meet your needs then someone should be thinking about how to change it so that it does.

2.  As a work-around, it is possible to select the desired network manually.  This is a pain but it might be your only short-term solution.

3.  Have a look at the 'wicd' package, which is a different network manager and is available at [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php).  Many others, including myself, have been persuaded to switch to this package because it works the way I want it to.

---

### Post by bscbrit on 2008-11-11
Sorry, I've missed the obvious - you have deselected the 'Start at Boot' option for your network?  Of course, this doesn't do what you asked and doing this means that it will never connect at Boot.  There isn't an option to 're-initialize the network to the way I left it'.

---

### Post by robert shearer on 2008-11-12
> Sorry, I've missed the obvious - you have deselected the 'Start at Boot' option for your network? 

Is there one???. I tried opening Preferences=>Network Configuration=>Auto Eth0=>Edit and deselecting "Connect automatically" but this only results in not being able to connect **at all** when using the "enable Networking" option on the Network Manager applet.

>  Of course, this doesn't do what you asked and doing this means that it will never connect at Boot.

Or any other time it seems.

 >  There isn't an option to 're-initialize the network to the way I left it'.

So I have found out. 

 There was in Hardy and now it has been dropped!!

'If it ain't broke don't fix it' and sometimes newer ain't better.

Thanks for your posts.

 Looks like I will file a bug report, 'cause it bugs me eh?

---

### Post by bscbrit on 2008-11-12
Yes, I agree with your sentiments.  I recall there was an option to 'Connect Automatically' but, as I have installed wicd and removed nm, I cannot check to describe it exactly or to test its functionality.  However, if it prevents you from connecting at all then I would say that it is another bug to add to your bug report.

I can't help but feel that there is a growing tendency to change things to use the latest bling 'because we can' rather than to leave things that work and are understood by the user alone.  I have stopped my upgrade of 7 computers to Intrepid after completing it on 4 machines with various problems.  I have even had to revert one of them back to Hardy.  Most people are content with the upgrade but I have tried to help people on this forum who are experiencing major network and display problems where there haven't been problems in the past.  To them and me, at least, Intrepid is not an improvement over Hardy.

I'm sorry that I couldn't help you to resolve this problem.

---

### Post by The Cog on 2008-11-12
Try using wicd instead. In my opinion, it's everything the network manager should have been but isn't. You will have to uninstall network manager to install wicd, but that's no great loss and you can easily revert if you don't like wicd.

You can get wicd from [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by bscbrit on 2008-11-12
I agree - see my post #2!

It does the job effectively and doesn't get in my way.

---

### Post by nothingspecial on 2008-11-12
+1 for wicd
And you don`t have to remove networkmanager, installing wicd from their repository does that for you.
Last time I looked they hadn`t made a Intrepid specific one but just use the Hardy one, it works fine.

---

### Post by robert shearer on 2008-11-16
Yes!... Thank you all for the **wicd** tip.

I have just installed it by adding this line to my sources.list

```
deb [http://apt.wicd.net](http://apt.wicd.net) intrepid extras
```

then...

```
wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add -
```

and...

```
sudo apt-get install wicd
```

I have yet to reboot and see if it behaves as I wish re the auto-connection BUT an immediate benefit is the **speed** at which it loads pages!!!

I will not be going back to network manager any-time soon.

Awesome.    thanks again.

---

### Post by frankleeee on 2008-11-16
> **The Cog said:**
> Try using wicd instead. In my opinion, it's everything the network manager should have been but isn't. You will have to uninstall network manager to install wicd, but that's no great loss and you can easily revert if you don't like wicd.

You can get wicd from [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

When you install it does a auto removal of network manager.

---

### Post by robert shearer on 2008-11-16
Oh...dog droppings!

Just rebooted and wicd would not connect at all.:(

Tried the suggestions on the wicd page.
Using  an 8 port switch and modem/router combination.

Had to uninstall wicd and re-install network-manager.

Back to square one... I have a network management app that cannot manage my network as I want it to **and** does it slowly but does connect, or I can install wicd which is fast but will not maintain a connection upon rebooting.

Dang.

Anything I could try?

Edit.... Reinstalled wicd and can now connect but the 'connect window' does not show the status. It continues to show the network as disconnected even when it **is** connected.

However, it does remember it's status on reboot- see the first post in this thread- so if I can get the applet to work then I can mark it as solved...

Any suggestions?

---

