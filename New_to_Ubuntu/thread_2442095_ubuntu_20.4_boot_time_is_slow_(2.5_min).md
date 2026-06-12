---
title: "ubuntu 20.4 boot time is slow (2.5 min)"
date: 2020-04-29
forum: New to Ubuntu
---

### Post by haribachala on 2020-04-29
[ATTACH=CONFIG]285686[/ATTACH]Hi,

I am new to ubuntu installed 20.4 today,but it taking around 2.5 mintues boot, also if i try to open any any application(browser, text editot ..etc) it taking 30s+.

system config:   dell- 4050, 8 gb, intel i5 2.4 Ghz(4)

can you please help me to fix this.

---

### Post by mastablasta on 2020-04-30
have you tried this in terminal?

```
 **systemd-analyze**
```

to see what the issue is. more here: [http://man7.org/linux/man-pages/man1/systemd-analyze.1.html](http://man7.org/linux/man-pages/man1/systemd-analyze.1.html)

the pic you attached is showing 45s boot time

---

### Post by haribachala on 2020-04-30
yes,it is 2+ min, attaching latest screenshot.

it taking more time to load user space, how to speedup this?

---

### Post by oldfred on 2020-04-30
See these threads.
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

You need to make sure UEFI firmware is most current.
If SSD make sure its firmware is most current.

These are primarily the tuning changes I made.
turned off NetworkManager-wait with systemctl
changed from quiet splash to noplymouth, will see boot process rather than Ubuntu logo
sudo apt install libblockdev-crypto2 libblockdev-mdraid2
turned off printer when rebooting
removed snaps

If UEFI firmware update not supported (yet), mine is not
sudo apt-get purge fwupd

---

### Post by cwmoser on 2020-05-02
Sort of a guess.  I have a Lenovo Thinkpad W510 Laptop that I recently purchased off Ebay.
It came with the 90w power supply.
I wrestled with slowness in the docking station, slow boot, network issues, etc and found it was
because I was using too low wattage power supply.  Went back to Ebay and purchased a
170w power supply to verify.

Not sure this is your issue, but googling tells me its a problem with more laptops than just Lenovo.
Just a FYI as a way out there guess.

---

### Post by aljames2 on 2020-05-02
I had this issue in 18.04.  What fixed it for me along with checking UEFI settings like @oldfred said.  But also disable all boot “things” showing in your boot priority list except your OS.  Mine was showing a boot order including my USB attached printer, & internal CD/DVD drive, & other attached “non-boot” storage drives.  Don’t just move these non-boot devices “down the priority list”...disable them in boot priority.

---

