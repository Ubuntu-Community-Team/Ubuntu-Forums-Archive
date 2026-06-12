---
title: "problems after installation stuck at terminal"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by pjim on 2012-06-03
Hi, I'm completely new to ubuntu but thought I'd give it a go. I downloaded the iso and made the boot cd. I had problems installing it, as the grub boot screen wouldn't appear going straight into windows. I managed to get past this by using the easybcd program from windows. However.. when I go to load ubuntu I get an ubuntu logo but then I just get to the terminal no gui. 

I don't know much to do. I have tried startx it tells me that there are problems with my nvidia gpu and that I should plug in the power cables to it? It says there are screens but no usuable configuration, then fatal error no screens found. 

I have an nvidia geforce 9600gt and also nvidia onboard graphics on my motherboard (which I don't use). The display worked fine from the trial function on the boot cd, got to a gui no problems.

Any advice appreciated.

---

### Post by sam_delta on 2012-06-03
if the live cd worked (the try function) there should be no problems running after installing. 
It is strange to me that you coulnt boot ubuntu after the install, 
what does easybcd do? the problem might have been from the install, maybe grub didnt installed correctly or something,
can you see the boot menu when booting? (try holding shift while booting).
are you installing alongside windows?

---

### Post by sandyd on 2012-06-03
> **pjim said:**
> Hi, I'm completely new to ubuntu but thought I'd give it a go. I downloaded the iso and made the boot cd. I had problems installing it, as the grub boot screen wouldn't appear going straight into windows. I managed to get past this by using the easybcd program from windows. However.. when I go to load ubuntu I get an ubuntu logo but then I just get to the terminal no gui. 

I don't know much to do. I have tried startx it tells me that there are problems with my nvidia gpu and that I should plug in the power cables to it? It says there are screens but no usuable configuration, then fatal error no screens found. 

I have an nvidia geforce 9600gt and also nvidia onboard graphics on my motherboard (which I don't use). The display worked fine from the trial function on the boot cd, got to a gui no problems.

Any advice appreciated.

are you connected to the internet via ethernet?
If you are, run this for me please:
```

sudo apt-get update
sudo apt-get install pastebinit
startx | pastebinit
```
post the output.

btw, there are a lot of problems with nvidia drivers on 12.04. If you want, you can do this.

1. At the grub screen (purple screen at bootup), if it doesn't show, press [shift] continuiously right after the BIOS screen.

2. Press 'e'

3. A the end of the line starting with 'linux' add 'nomodeset' (no quotes, space in front)

Press control+X to boot.

---

### Post by pjim on 2012-06-06
thanks for the response. 

Yes I installed alongside windows, the easybcd enabled me to use the windows bootloader to get to the grub screen. Which I can get to yes.

When I used the try function on the cd I had to check nomodeset to get it to work.

I have tried adding the "nomodeset" at the end of the line starting linux thanks, however it still goes to the terminal.

I've done this no problem: sudo apt-get update
sudo apt-get install pastebinit
startx | pastebinit

The output was the same as before. Saying about plugging in the nvidia gpu then saying fatal error no screens found.

I'll have to write it down to put it on here, as I need to get to windows to post. Thanks again.

---

### Post by choppyfireballs on 2012-06-06
> **pjim said:**
> Hi, I'm completely new to ubuntu but thought I'd give it a go. I downloaded the iso and made the boot cd. I had problems installing it, as the grub boot screen wouldn't appear going straight into windows. I managed to get past this by using the easybcd program from windows. However.. when I go to load ubuntu I get an ubuntu logo but then I just get to the terminal no gui. 

I don't know much to do. I have tried startx it tells me that there are problems with my nvidia gpu and that I should plug in the power cables to it? It says there are screens but no usuable configuration, then fatal error no screens found. 

I have an nvidia geforce 9600gt and also nvidia onboard graphics on my motherboard (which I don't use). The display worked fine from the trial function on the boot cd, got to a gui no problems.

Any advice appreciated.

Have you tried using your onboard gpu for the time being so you can at least use the cpu

---

