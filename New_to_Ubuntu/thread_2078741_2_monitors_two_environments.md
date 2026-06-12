---
title: "2 monitors two environments"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by chathamBoy on 2012-10-31
Hi

I have a desktop machine that I use in 2 locations, namely home and office. Each location has dual screens. After installation of Ubuntu 12.04 I set up my home environment to use both screens and saved the set up to the config file. When I used my machine at the office I had to reconfigure the set up for those screens which are different models to my home set up. I again saved the set up, but when booting back at home I realized that office set up had overwritten the home set up. Is there a way to save both set ups and auto-detect the environment or to run a script from the command line to set up the screens for each location?

Many thanks in advance.

---

### Post by chathamBoy on 2012-11-05
Please can someone help, really stuck here. Am I wording this incorrectly or should I add more information?

Thanks

---

### Post by MG&amp;TL on 2012-11-05
I don't think anyone (so far) knows how to do what you're doing, which is the problem. 

How are you accessing the machine from work?

---

### Post by chathamBoy on 2012-11-05
Hi MG&TL

Thanks for the reply. I guess this is unusual but I transport my PC between home and work, I just don't do laptops. So the my workstation at home has two screens and the same at my office. Just wondered if there was a way to save both configs for the twin setup and load either at each location. Can I invoke an X-config from the terminal? Hope this makes sense.

Cheers.

---

### Post by MG&amp;TL on 2012-11-05
> **chathamBoy said:**
> Hi MG&TL

Thanks for the reply. I guess this is unusual but I transport my PC between home and work, I just don't do laptops. So the my workstation at home has two screens and the same at my office. Just wondered if there was a way to save both configs for the twin setup and load either at each location. Can I invoke an X-config from the terminal? Hope this makes sense.

Cheers.

Oh, okay. Unusual, but each to their own. :)

I believe xrandr run on desktop startup would work just fine. See this answer:  [http://askubuntu.com/questions/107085/how-to-set-resolutions-with-xrandr-using-multiple-monitors]("http://askubuntu.com/questions/107085/how-to-set-resolutions-with-xrandr-using-multiple-monitors").

Just put two separate launchers on the desktop or something. :)

---

### Post by chathamBoy on 2012-11-06
Hi MG&TL

Thanks again for the reply. Unfortunately it says xrandr does not work with proprietary drivers, but really appreciate the help.

Cheers

---

### Post by MG&amp;TL on 2012-11-06
Right...in which case, what proprietary drivers are you running?

---

