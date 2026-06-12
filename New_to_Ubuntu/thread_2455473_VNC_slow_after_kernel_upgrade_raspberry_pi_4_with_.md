---
title: "VNC slow after kernel upgrade raspberry pi 4 with ubuntu 20.10"
date: 2020-12-20
forum: New to Ubuntu
---

### Post by kazin08 on 2020-12-20
Hello all!

I have an issue after upgrading the kernel 5.8.0-1007 to 5.8.0-1008 and above, my connection using VNC viewer to my raspberry pi 4 using ubuntu 20.10 was really slow, and this occur when I move the mouse. I use my pi headless, and before upgrading the kernel I doesn't had this issue. Can someone explain me why this happen to me?

I have a video to show this issue:
[https://youtu.be/d0rLwWov860](https://youtu.be/d0rLwWov860)

Hope someone can help me,

Best regards!

---

### Post by TheFu on 2020-12-20
Is this a joke?  You really expect a video to work over VNC?  Seriously?  I'm 100% serious, btw.  That's just crazy.  

If you want remote video, use SPICE.  It is trivial to work under KVM/libvirt, but people have gotten it working under lxd [https://discuss.linuxcontainers.org/t/access-container-via-spice-sharing-clipboard/2544](https://discuss.linuxcontainers.org/t/access-container-via-spice-sharing-clipboard/2544)  I've not tried that, but may.  I just use many VMs and not so many physical systems.

Or on the same LAN, why not use remote X/Windows directly? It has been possible for 30+ yrs.  This is part of X11, though using ssh to create a channel per application is much easier.
[https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)

---

### Post by kazin08 on 2020-12-20
[COLOR=#333333][FONT=&amp]I'm not expecting to view videos using VNC [/FONT][/COLOR][COLOR=#333333][FONT=&amp]hahah[/FONT][/COLOR][COLOR=#333333][FONT=&amp] because yes, that's crazy. 

I'm using my pi to program and take advantage of the GPIO.
The video I made is to see what happen when I move the mouse, the image freezes for a second or two, every time I move the mouse, but this doesn't happened with kernel 5.8.0-1007. That's what give me crazy to find a solution.

I'm using this on my LAN network through Ethernet, so the network isn't a problem.I'll try the suggestion of [/FONT][/COLOR][COLOR=#333333][FONT=&amp]ssh[/FONT][/COLOR][COLOR=#333333][FONT=&amp] to see. 
Sorry if I explain my error wrong.

Regards[/FONT][/COLOR]

---

### Post by TheFu on 2020-12-20
That video link has fish swimming around.  That will eat all the bandwidth for any VNC desktop.  I didn't notice any pointer since 20+ fish were swimming.

Remote X11 doesn't provide a desktop. It provides 1 application at a time.

---

### Post by kazin08 on 2020-12-20
Yes, my bad, you can start the video here to take a better look:

[https://youtu.be/d0rLwWov860?t=60](https://youtu.be/d0rLwWov860?t=60)

As you can see, when I move the mouse, the network traffic drop to 0 and the video frezzes.

Thanks for your reply.

Best regards.

---

### Post by ActionParsnip on 2020-12-21
If you want to stream video from a Pi, just install openssh-server. Mount the SFTP service that this gives and play the media on a local player streaming the data from the Pi. VNC will not stream audio and video.

---

### Post by kazin08 on 2020-12-21
> **ActionParsnip said:**
> If you want to stream video from a Pi, just install openssh-server. Mount the SFTP service that this gives and play the media on a local player streaming the data from the Pi. VNC will not stream audio and video.

Thanks for your reply! but no, I don't want to stream videos on my pi. I only want to use it as a headless desktop to use vs studio and other things that don't need a lot of consumption, because my main idea is to use it outside my house (not always) with my VPN. 

Again, thanks for your suggestion!

Can anyone tell me how can I go back to kernel 5.8.0-1007? Because I tried without success.

Best regards!

---

### Post by ActionParsnip on 2020-12-21
Hold SHIFT at boot and you can select the older kernel.

---

### Post by kazin08 on 2020-12-21
> **ActionParsnip said:**
> Hold SHIFT at boot and you can select the older kernel.

That's not possible on the pi. Pi don't use grub at boot, so it has to be in another way!

Regards

---

### Post by TheFu on 2020-12-21
> **kazin08 said:**
>   I only want to use it as a headless desktop to use vs studio and other things that don't need a lot of consumption, because my main idea is to use it outside my house (not always) with my VPN.  

For remote desktop when I travel, I use x2go. It uses the NX protocol that leverages ssh and the GUI performance is 2-3x faster than any VNC. I don't know whether there is an x2go-server for ARM, however. 
[https://wiki.x2go.org/doku.php/doc:installation:x2goserver#raspbian](https://wiki.x2go.org/doku.php/doc:installation:x2goserver#raspbian)
Looks like they have it for Raspbian.

Also, I know of 20.04 is the x2go-server, they broke something with ssh-key authentication. A password seems to be required even if ssh-keys are setup and working.  I've not seen that on any other releases.  Don't know about 20.10.  That's too new for me and not an LTS.

---

### Post by kazin08 on 2020-12-21
I tried X2go. I can install in ubuntu 20.10 and have an ARM deb. But I use gnome 3.38 that is not supported by X2go.

I will try again to install older kernel and see if I can use it, at least for now.

How can I report this problem to the kernel devs?

Regards

---

### Post by TheFu on 2020-12-21
I'm more of a practical advisor suggesting what I know works. But if you want to wait months for a solution, if ever, open the bug.

gnome 3.38?  Don't use that for remote desktops.  Gnome3 is a hog. It wants direct access to the GPU and remote desktops don't provide that. I suspect it also wants us to run Wayland, not X11.

Use a lighter DE.  That would be step #1.  Use XFCE or LXQt for remote desktops, if you need any DE at all.

I use other openbox or fvwm without DEs.  Gnome3 is known to be terrible for remote desktops, which is why it isn't supported.  I do recall that the Gnome team was working on ubuntu-to-ubuntu remote desktops which would would with Gnome3, but that project stalled. [https://wiki.gnome.org/Projects/Mutter/RemoteDesktop](https://wiki.gnome.org/Projects/Mutter/RemoteDesktop) is the link.
> Currently only remote passwordless unencrypted VNC access to an existing session is supported
which makes it unsuitable for your needs.

You can report issues using **apport-bug**.  You can use Canonical's bug reporting website too.  I've never used it. A google search will find it quickly. Nobody here works for Canonical, BTW.  Canonical will look over the bug and ask you to do some things - usually the first request will be that you run the latest kernel which you'll need to build for ARM ... some 5.11.x version to prove it hasn't magically been fixed. Assuming it isn't fixed, it will be passed to the upstream project, Debian, who will do the same (probably), then pass it up to the kernel.org guys and Linus. This assumes it is a kernel issue and not just a regression due to VNC or Gnome or one of 50 other projects between VNC and the kernel.  They might ask you to reproduce it on non-ARM hardware too.

I really think you got lucky with the other kernel working with gnome3. It was probably a fluke that it did.

---

### Post by kazin08 on 2020-12-21
Thank you again TheFu for your advices!

Yes I know that other DE are lightier than gnome. Maybe yes, the solution is to use one lighter than wait for a new kernel. In another hand, I tried the kernel 5.9 using another image and doesn't have this problem. But I cannot install that kernel on my current ubuntu (It always giveme errors), so I'll need to install all again, from scratch (my configurations, programs, etc) in the new image.

Also thanks for help me to understand how can I report a bug and all the steps that are involved in it.

Best regards!

---

