---
title: "sound options and display problem"
date: 2022-10-26
forum: New to Ubuntu
---

### Post by phillip1882 on 2022-10-26
i used to be able to select hdi tv as a sound option, and that worked but it's no longer there.
also i used to get several screen resolution options but now i'm only getting one that leaves the left sidebar too far to the left and mostly off screen.

---

### Post by Autodave on 2022-10-26
You need to give us some more info please:

What version of 'buntu are you using?
What graphics card are you using?
How is the TV/monitor connected to the computer?
Laptop or desktop?

---

### Post by phillip1882 on 2022-10-31
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.5 LTS
Release:	20.04
Codename:	focal

01:00.0 VGA compatible controller: NVIDIA Corporation GP107 [GeForce GTX 1050 Ti] (rev a1)

HDMI to DVI port

desktop

---

### Post by MAFoElffen on 2022-10-31
Please run the UbuntuForums 'system-info' script in "detailed mode":
```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info -d

```
Select UpLoad to PasteBIN and post the URL for us to look at.

In "Detailed Mode" it will give a detailed report on things such as Sound and Video hardware and settings... to include what is being used as device drivers. I think that is a good start.

---

### Post by phillip1882 on 2022-10-31
[https://pastebin.com/STCcadAz]("https://pastebin.com/STCcadAz")

---

### Post by MAFoElffen on 2022-10-31
> **phillip1882 said:**
> [https://pastebin.com/STCcadAz](https://pastebin.com/STCcadAz)

What the heck? That is the source code of the script.. Did you run It? (with startup option "-d")

---

### Post by MAFoElffen on 2022-11-01
Now that you have the script downloaded, if you go to the directory you downloaded to with the file manager, right click on the script > Properties > Permission > Ensure the "Execute" checkbox is checked... Then close the properties.

[s]Double click on the script.[/s] 

<EDIT>Open a terminal session. Navigate to where the script was downloaded.
```

./system-info -d

```
[s]It will open a terminal session[/s], and follow the prompts... At the end, when it asks you to upload to a pastebin, say "Y" for yes... Copy the link to a post.

---

