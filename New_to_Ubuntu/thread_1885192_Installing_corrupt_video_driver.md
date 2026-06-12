---
title: "Installing corrupt video driver"
date: 2011-11-22
forum: New to Ubuntu
---

### Post by lauribuntu on 2011-11-22
G'day.

I have had problems with my 11.10 ubuntu after changing a video card. (posted a thread recently about it). Card change was a necessity after it's cooling fan gave up.. Installed the replacement nvidia 6800GT I had on hand. Worked fine until I deleted all the video drivers in 'additional software' tab on system settings (thought I'd get the dual monitor thing going...or so I thought..and read doing this would get it working...should have left well enough alone...). This meant I got the famous 'black screen' after rebooting..... 

Anyway after rebooting problems happened. I couldn't access grub, but fixed that with 'Boot Repair', finally got into recovery mode and tried the 'repair packages' option. That did not work, But I now can boot into console text mode (I think that's the correct name).

Now from here I really want to try and update my video drivers.. I have tried many way from what I have learned here (using the excellent posts from MAFoElffen - " Graphics resolution - upgrade/blank screen after reboot), and searching the Internet.

After doing this:

```
sudo apt-get update
sudo nvidia-installer --uninstall 
sudo apt-get remove nvidia-* 
sudo apt-get install 'uname -r' 
sudo apt-get install nvidia-current   
sudo nvidia-xconfig 
sudo apt-get update
```I get errors after I perform that. After, I still can't start this: (which is the next step):)

```
sudo service gdm start

```So, I think the problem is :

a) how can I purge the old drivers?
b) what is the best way to download/reinstall them?
c) Or is it better to use a Ubuntu driver - not a propriety Nvidia one?

Help!!

Thanks.

L.

---

### Post by neofreud on 2011-11-23
Hello, 


What are the errors that you are getting? 

> 3) Is it better to use ubuntu drivers?

It depends on what you are trying to do. Do you do a lot of video editing, heavy gaming, video resource hungry stuff? If not then most of the time you can use the default drivers with no issues at all.

---

