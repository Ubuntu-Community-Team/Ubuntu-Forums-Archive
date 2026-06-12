---
title: "No sound!"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by Shadius on 2012-07-08
Hey everybody! :) 

I've recently installed Ubuntu 12.04 on my system, but I have no sound! :( I've checked if the speakers were on mute and the obvious things, but those were fine. How do I solve this issue?

---

### Post by NikTh on 2012-07-08
Did you try ```
sudo alsa force-reload
```

Also you can check 
```
 cat /proc/asound/card0/codec* | grep Codec
``` to see what is your card codec. ```
cat /proc/asound/modules 
``` to see card module..Then you can check out your card model here  ```
zcat /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz
``` and try to set the correct parameter in ```
 
sudo nano /etc/modprobe.d/alsa-base.conf
``` with **options <your card model> MODEL=what did you find in HD-Audio-Models.txt**

You can also set parameter **MODEL=auto** . Its a generic parameter that works sometimes.. 

Check the documentation here > [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by Shadius on 2012-07-08
Thank you. I'll try these out.

---

### Post by Shadius on 2012-07-08
> **NikTh said:**
> Did you try ```
sudo alsa force-reload
```

Also you can check 
```
 cat /proc/asound/card0/codec* | grep Codec
``` to see what is your card codec. ```
cat /proc/asound/modules 
``` to see card module..Then you can check out your card model here  ```
zcat /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz
``` and try to set the correct parameter in ```
 
sudo nano /etc/modprobe.d/alsa-base.conf
``` with **options <your card model> MODEL=what did you find in HD-Audio-Models.txt**

You can also set parameter **MODEL=auto** . Its a generic parameter that works sometimes.. 

Check the documentation here > [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Thank you very much!! Running the first command worked! Just so I understand and can help myself if this ever happens again, running that first command reloads the ALSA?

---

### Post by NikTh on 2012-07-08
> **Shadius said:**
>  running that first command reloads the ALSA?

Yes. Basically **force**-reloads Alsa modules .

---

### Post by Shadius on 2012-07-08
> **NikTh said:**
> Yes. Basically **force**-reloads Alsa modules .

Thank you. Also, when I ran the second code, it gave me this:
```
shadius@shadius-asus:~$ cat /proc/asound/card0/codec* | grep Codec
cat: /proc/asound/card0/codec97#0: Is a directory
shadius@shadius-asus:~$ 


```

What does this mean? Wasn't it supposed to show some codec?

---

### Post by NikTh on 2012-07-08
> **Shadius said:**
> Also, when I ran the second code, it gave me this:
```
shadius@shadius-asus:~$ cat /proc/asound/card0/codec* | grep Codec
cat: /proc/asound/card0/codec97#0: Is a directory
shadius@shadius-asus:~$ 


```What does this mean? Wasn't it supposed to show some codec?

Yes , its supposed to return something like this.. 
```
 cat /proc/asound/card0/codec* | grep Codec
[COLOR=Red]Codec[/COLOR]: Realtek ALC892
```Maybe you card's codec its in another card than card0. Try to use the command with Tab key ... ```
cat /proc/asound/ # and here use Tab key to list your available card directories
```  Try other card directories accordingly.

OR

try Tab key with current loacation .. ```
cat /proc/asound/card0/ # Tab key here.. 
```

---

### Post by Shadius on 2012-07-08
> **NikTh said:**
> Yes , its supposed to return something like this.. 
```
 cat /proc/asound/card0/codec* | grep Codec
[COLOR=Red]Codec[/COLOR]: Realtek ALC892
```Maybe you card's codec its in another card than card0. Try to use the command with Tab key ... ```
cat /proc/asound/ # and here use Tab key to list your available card directories
```  Try other card directories accordingly.

OR

try Tab key with current loacation .. ```
cat /proc/asound/card0/ # Tab key here.. 
```

Okay, here's what I got:
```
shadius@shadius-asus:~$ cat /proc/asound/
Audigy/  card1/   cards    hwdep    modules  pcm      timers   version
card0/   card2/   devices  ICH5/    oss/     seq/     UART/    
shadius@shadius-asus:~$ cat /proc/asound/cat /proc/asound/card0/
codec97#0/ intel8x0   pcm0p/     pcm2c/     pcm4p/     
id         pcm0c/     pcm1c/     pcm3c/     
shadius@shadius-asus:~$ cat /proc/asound/cat /proc/asound/card0/

```

What's this all mean?

---

### Post by NikTh on 2012-07-09
> **Shadius said:**
> Okay, here's what I got:
```
shadius@shadius-asus:~$ cat /proc/asound/
Audigy/  card1/   cards    hwdep    modules  pcm      timers   version
card0/   card2/   devices  ICH5/    oss/     seq/     UART/    
shadius@shadius-asus:~$ cat /proc/asound/cat /proc/asound/card0/
codec97#0/ intel8x0   pcm0p/     pcm2c/     pcm4p/     
id         pcm0c/     pcm1c/     pcm3c/     
shadius@shadius-asus:~$ cat /proc/asound/cat /proc/asound/card0/

```What's this all mean?

I am not sure but i think means that you can try to find you card's codec in another card directory , like card1/ or card/2 
e.g: 
```
cat /proc/asound/card1/codec*  | grep Codec
```

---

### Post by Shadius on 2012-07-09
> **NikTh said:**
> I am not sure but i think means that you can try to find you card's codec in another card directory , like card1/ or card/2 
e.g: 
```
cat /proc/asound/card1/codec*  | grep Codec
```

Oh okay, well, thanks for helping me get my sound working!

---

