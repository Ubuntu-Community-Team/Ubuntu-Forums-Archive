---
title: "Help with bash script"
date: 2014-03-15
forum: New to Ubuntu
---

### Post by sujitrjadhav on 2014-03-15
Hi,

I have a file with name links.txt which have some urls on each line. I need to write a bash script which read each line from the file links.txt then concatenate the read url with text "https://www.facebook.com/sharer/sharer.php?" and open the concatenated url in the browser. In short I need to write a bash script which reads some urls from file links.txt and post the urls to facebook

what command do I write?

Thanks in advance.

---

### Post by steeldriver on 2014-03-15
A good general structure would be something like

```

while read -r line
do 
    *something with *"$line"
done < *yourfile*

```

---

### Post by sujitrjadhav on 2014-03-15
Thanks Very Much Steeldriver. It solved my problem.

---

