---
title: "Video player not working."
date: 2012-07-29
forum: New to Ubuntu
---

### Post by Zundap on 2012-07-29
Hi, i have recently installed OBUNTU 12.04 but i cant play DVD's, when i put a film in the drive, the computer sees it ok and gives a dialogue box saying as below.                                   
**An error occured**
 "Could not read DVD.  This maybe because the DVD is encrypted and a decryption library has not been installed"



Could any tell me how to cure this problem?    I have also tried VLC and that wont work either. Thanks in advance.

---

### Post by Laiquendi on 2012-07-29
try:
```
sudo apt-get install libdvdcss2 && sudo /usr/share/doc/libdvdread4/./install-css.sh
```

---

### Post by cogier on 2012-07-29
Go to Medibuntu here [http://medibuntu.org/repository.php]("http://medibuntu.org/repository.php")

Copy the code starting "sudo -E wget --outpu.....". 

Open a Terminal session by pressing **[Ctrl] + [Alt] + T**

Paste the code in to Terminal with **[Ctrl] + [Shift] + V**

Press [Enter] if required and enter your password when asked.

Once finished restart whatever programme you are using to play the DVD and hopefully that will be that.

(This will process will also add extra "non-free" items to the Software Centre)

---

### Post by Zundap on 2012-07-29
Thanks Laiquendi and cogier, i have tried both your commands and with both i get **"command not found"** 

Any other idea's would be greatly apreciated.

---

### Post by ajgreeny on 2012-07-29
For full details and info read [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs/](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs/)

---

### Post by Zundap on 2012-07-29
> **ajgreeny said:**
> For full details and info read [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs/](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs/)

Thanks aqjgreeny i'll give it a go.

---

### Post by Zundap on 2012-07-29
I have just had a quick look at the link you gave me ajgreeny and Sheeeeesh, it aint  half technical, i am going to have to study this lot and i don't have much confidence in doing that. 
So far as i have read, it goes over my head, far too technical for beginners i would have thought. I have been using computers for 8 years or so and ubuntu for a couple of years and the link is very hard going for me, God help the new  starters, they aint got a virgin  in hells chance. 

I read some where that ubuntu team's aim was to simplify it for the ordinary guy in the street, to challenge Windows (spit) in effect. With great deserved  respect to the ubuntu team, If that is the case, then the ubuntu team have just taken a dozen or more backward steps. The ordinary guy in the street can not follow the instructions in that link.

I am though a trier if nothing else and i will get struck in to it and hope i get the hang of it.  Thanks again for the link, its greatly appreciated.

---

### Post by ajgreeny on 2012-07-30
[FONT=Verdana]You don't really need to worry about all that being over your head.

Open a terminal with Ctrl+Alt+T and in that type ```
sudo apt-get install libdvdread4
```Type your password, which you will not see shown in terminal but it will be there so don't worry.

When that has installed the libdvdread4 package, in the same terminal type [/FONT][FONT=Verdana]```
sudo /usr/share/doc/libdvdread4/install-css.sh
```Enter your password again if needed and that should do what you need.[/FONT]

---

