---
title: "script which writes from html- site to openoffice"
date: 2008-02-07
forum: Programming Talk
---

### Post by schnuser on 2008-02-07
Hi everyone

I am relatively new to linux and its related stuff, nevertheless ive tried to solve my little project on my own, but I think without some help I do not get through.
I wanna do this:
A script which by its launch downloads the HTML Code of a specific site "www.somesite.com" (probalby with wget). In the HTML code will be a sequence like this:

  > <table class="aceq_labValBox" id="aceq_labValBox_lines" border="0" cellpadding="0" cellspacing="0">
    <tbody><tr>
      <td>**Last**:</td>
      <td class="**value**"><b>_**26.04**_</b></td>
      <td style="padding-left: 20px;">On last volume:</td>

      <td class="value"><b>1'368</b></td>
      <td class="value" width="100%">(17:30:28)</td>
    </tr>
You see in bold the word "Last" (i edited this manually for illustration purposes), underneath the word "value" followed by the digit "26.04" (this has somewhat to do with share prices). 
Now I wana copy this digit into a specific cell of openoffice calc. 

There I wanna make some charts and analysis on my own.

Can you please give me some hints and advice how I could solve this task?
regards

---

### Post by ghostdog74 on 2008-02-07
tested only on the sample
```

awk '/<td>Last:<\/td>/{
 getline;
 val=gensub(/.*<b>(.*)<\/b>.*/,"\\1","g")
 print "this is your value: " val
}' file

```

---

### Post by pmasiar on 2008-02-07
I would suggest doing whole thing in Python: download with urllib2, parse HTML with ElementTree or BeautifulSoup (or even manually), and generate either tab-delimited file or there should be some package to write Excel files IIRC, but I forgot the name.

And Python is universal language, you can use it later for other things.

---

### Post by schnuser on 2008-02-08
Thanks a lot for your replies. I'll work with the "gawk- solution" because i dont know python yet (this may hopefully change someday).
Now I have to think about how to get "val" into oocalc (suggestions appreciated).

Thank you

---

### Post by ghostdog74 on 2008-02-08
oocalc can open csv file. so you can just output your val as comma separated values and open it with oocalc

---

### Post by [h2o] on 2008-02-08
There is also a Python API for OpenOffice. The documentation is not very good but it works quite well when you get the hang of it.
But if using a CSV-file works for you then that's what you should use.

---

### Post by schnuser on 2008-02-08
> **ghostdog74 said:**
> oocalc can open csv file. so you can just output your val as comma separated values and open it with oocalc

Yes this will work, cool.
Thanks

---

