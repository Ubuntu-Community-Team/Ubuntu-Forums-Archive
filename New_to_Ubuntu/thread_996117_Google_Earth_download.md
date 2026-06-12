---
title: "Google Earth download"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by annakalsi on 2008-11-28
Hi

I have tried to downloadoogle Earth and I get the following error message:

Could not open the file /home/anna/Desktop/GoogleEarthLinux.bin.part using the Unicode (UTF-8) character coding.

Can anyone help please.

Thanks

---

### Post by ubuntu27 on 2008-11-28
What version of Ubuntu are you running?

I am going to post the solution for the_ latest version_ (Ubuntu 8.10 ). 

I you have another version, please [visit this Guide]("https://help.ubuntu.com/community/Medibuntu").


Open the Terminal which is located at Applications menu/Accessories/Terminal

Now copy and paste the following commands:
```

sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Now that you have the medibuntu repository, you can find Google Earth.

You can install Google Earth with Synaptic Package Manager or with terminal. 
The command for the terminal is

```
sudo apt-get install googleearth
```

That's it. 

Good Luck!

---

### Post by residualbit on 2008-11-28
Also, if the file extension is bin.part, it is only a partial file and was not finished downloading.

---

