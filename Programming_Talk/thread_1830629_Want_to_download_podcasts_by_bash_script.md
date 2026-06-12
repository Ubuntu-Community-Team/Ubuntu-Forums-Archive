---
title: "Want to download podcasts by bash script"
date: 2011-08-22
forum: Programming Talk
---

### Post by Praveen30 on 2011-08-22
Everyday i have to go to sites to download my podcast but i have heard this process can be automated with the help of scripts..so can anyone suggest me how to make a script to download podcasts, consider me as a rookie in bash scripting..so any tutorial will also be good..

---

### Post by fdrake on 2011-08-22
> **Praveen30 said:**
> Everyday i have to go to sites to download my podcast but i have heard this process can be automated with the help of scripts..so can anyone suggest me how to make a script to download podcasts, consider me as a rookie in bash scripting..so any tutorial will also be good..

```

cd ~
mkdir podcast
cd ./podcast
cat > podcast.sh
#!/bin/bash
wget http://mysite.com/mypodcast
<press control +D>
chmod +x podcast.sh

```
you can add to eecute the script on a crontab . does the name of the podcast has any kind of structure (like podacadst.12-02-2011)?

---

### Post by jrogers360 on 2012-02-02
podcast URL's are just an XML file pointing to the most recent files to download (think RSS)

OP should try to download package podracer, and use that to download podcasts.

---

