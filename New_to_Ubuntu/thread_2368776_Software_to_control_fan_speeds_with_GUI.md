---
title: "Software to control fan speeds with GUI?"
date: 2017-08-14
forum: New to Ubuntu
---

### Post by allanwatts87 on 2017-08-14
Hello, I'm still relatively new to Ubuntu and working with the terminal, and I was wondering if there was a software with a simplified GUI I could use to cap my laptop's fan speeds to around ~2000 RPM, maybe a little less.
Currently my fans' bearings are worn out and can sometimes make a loud buzzing sound which is extremely annoying. I want to prevent them from getting to certain speeds that can generate this irritating noise. I was hoping I could get any links or applications on the software store that would help me.
Thanks in advance.

---

### Post by Futant on 2017-08-15
Hi, welcome to the forum! I don't think there are any gui methods for changing fan speeds, there are ways using the terminal but it is not a trivial matter, and methods vary depending on hardware and software. If your fan isn't working properly, it would be best to replace it. In the meantime you could try [reducing]("https://itsfoss.com/reduce-overheating-laptops-linux/") the running temperature of your laptop. 

If your fan is constantly running at full speed, there might be a way to sort it out but for any further help we need to know what hardware you are using and your *buntu version.

Also, don't be scared of the terminal! With some research and sensible practices it can be your best friend :)

---

### Post by Frogs Hair on 2017-08-15
Hello and Welcome

Some information about you hardware could be useful. I have a graphics card in one computer that requires a proprietary driver to keep the fan running properly with Linux. Can you post the output of the following. ```
lspci -v
```

---

