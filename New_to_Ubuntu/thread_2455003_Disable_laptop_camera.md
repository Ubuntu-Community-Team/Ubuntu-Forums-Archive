---
title: "Disable laptop camera"
date: 2020-12-10
forum: New to Ubuntu
---

### Post by saif1alsaad on 2020-12-10
Hello, how can I lock or disable the camera using terminal ?? Also how can I know if the laptop is using my camera ? And when I need the camera how to enable it ?? 
thank you :)

---

### Post by CatKiller on 2020-12-10
Personally, I would trust a small piece of electrical tape more than any software solution.

---

### Post by saif1alsaad on 2020-12-10
lol I agree with you....I used to that but its cooler way to disable it from terminal I feel like a cool man :)

---

### Post by ActionParsnip on 2020-12-10
If you unload the uvcvideo kernel module it should do it. I use this
[https://tinyurl.com/W3bCamCover](https://tinyurl.com/W3bCamCover)

Works well

---

### Post by SeijiSensei on 2020-12-10
Usually there is an LED near the camera that lights up when it is in use. I believe this is a pretty standard feature once news spread that hackers were using laptop cameras to spy on unsuspecting victims.

---

### Post by saif1alsaad on 2020-12-10
Yes I have this feature.... Does some create an action that pervert the LED from turning on ??
and thank you to inform me :)

---

### Post by saif1alsaad on 2020-12-10
My friend was looking for these.. I think this peace is very good to cover your camera
But as I said I want to use terminal to look cool :)

---

### Post by ActionParsnip on 2020-12-10
```

sudo modprobe -r uvcvideo

```

Should do it. You can test applications before running the command and after the command to make sure there is no webcam device after you unload the module.

---

### Post by saif1alsaad on 2020-12-10
Thank you so much <3 :)

---

### Post by saif1alsaad on 2020-12-10
> **ActionParsnip said:**
> ```

sudo modprobe -r uvcvideo

```

Should do it. You can test applications before running the command and after the command to make sure there is no webcam device after you unload the module.



How can i open it again :)))))

---

### Post by SeijiSensei on 2020-12-10
Run the same command without the "-r" switch.

See: [https://linux.die.net/man/8/modprobe](https://linux.die.net/man/8/modprobe)

---

### Post by saif1alsaad on 2020-12-10
> **SeijiSensei said:**
> Run the same command without the "-r" switch.

See: [https://linux.die.net/man/8/modprobe](https://linux.die.net/man/8/modprobe)


Thank you so much <3

---

### Post by TheFu on 2020-12-10
> **SeijiSensei said:**
> Usually there is an LED near the camera that lights up when it is in use. I believe this is a pretty standard feature once news spread that hackers were using laptop cameras to spy on unsuspecting victims.

Looking a the camera api a few years ago, it was clear that turnng on the LED is a separate call.  Completely optional and not tied electrically to the CCD being used.

Use a physical barrier.
Also, I don't know of any method the ensure the audio microphone is not connected.

If a driver can be unloaded, then it can be loaded as well. Certainly, use multiple techniques, but in the end, a physical barrier is still required.

---

### Post by saif1alsaad on 2020-12-10
> **TheFu said:**
> Looking a the camera api a few years ago, it was clear that turnng on the LED is a separate call.  Completely optional and not tied electrically to the CCD being used.

Use a physical barrier.
Also, I don't know of any method the ensure the audio microphone is not connected.

If a driver can be unloaded, then it can be loaded as well. Certainly, use multiple techniques, but in the end, a physical barrier is still required.


The Audio is ok for now
and the LED is working well as they said if its on use it will turn on
of course why not using multiple methods :)

---

### Post by TheFu on 2020-12-10
> **saif1alsaad said:**
> The Audio is ok for now
and the LED is working well as they said if its on use it will turn on
of course why not using multiple methods :)

I think you misunderstand.  If someone wants to video record you and can 
a) find a bug in the program you use
b) swap out the program with one they wrote

Then the LED won't necessarily turn on when recording/streaming/the CCD is used.

On my desktop, I physically unplug my webcam when it isn't actively used. When I first plug it in, I point it at the ceiling.
On my laptops, I have a webcam slider that covers the camera that was swag at some Linux conference a few years ago. It is always closed.

[https://www.theregister.com/2020/12/11/christopher_taylor_webcam_perv_extradition_case/](https://www.theregister.com/2020/12/11/christopher_taylor_webcam_perv_extradition_case/) fresh from the headlines today.

---

### Post by saif1alsaad on 2020-12-15
now I understand you
yeah you got a point 
Thank for your information <3

---

### Post by XBMC old School on 2020-12-19
I don't know how helpful this will be but, you could create a new compiled kernel with all the drivers related to webcams, usb, etc removed, and have it in as a grub option. assurance & flexability.  I used to do kernel modding back in 10.04 but I couldn't tell you how to do it now.

---

