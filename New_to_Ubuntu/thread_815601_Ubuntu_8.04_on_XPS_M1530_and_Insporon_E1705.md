---
title: "Ubuntu 8.04 on XPS M1530 and Insporon E1705"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by wak_wak on 2008-06-01
Just wanted to take a minute to commend and thank those involved for a terrific release.

I've installed Ubuntu on both of my laptops (listed above) and barring a little tweak for the XPS and the touchpad it's bar none the best OS I've ever used.

Everything works great.  Video was a snap, sound was perfect and wireless support phenomenal.  

If anyone needs it, on the XPS M1530, you'll need to plug in a USB mouse and do the following to get it going properly:

you must add i8042.nomux=1 in the kernel line before where it says splash.
after the change, the line should look something like this:
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=3fced842-2be9-413d-802e-4da2e19ccdc1 or quiet i8042.nomux=1 splash
or you can also look at the screenshot I have attached to this post.
this will surely fix the speed and craziness of your touchpad.

I found that in another post.

I was also able to speed up the internet a bit by updating the DNS servers:

Step 1:Go to Applications->Accessories->Terminal and type
sudo gedit /etc/dhcp3/dhclient.conf . You will be asked to type in the sudo password.After which the dhclient.conf file will open
Step 2:This is where you enter the DNS information.Go to the end of the file and add the following line to the END of the file
prepend domain-name-servers 208.67.222.222,208.67.220.220;
Step 3:Save the file and close it.
Step 4:Thats all, now you will be using opendns servers whenever you use the internet

Once those two tweaks were done I had a perfectly performing laptop.  Even the remote worked!

So thanks!

---

