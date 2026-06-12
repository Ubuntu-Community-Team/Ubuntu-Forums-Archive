---
title: "WGET a list of urls to a particular folder on desktop via command line?"
date: 2012-06-18
forum: New to Ubuntu
---

### Post by bostoncab on 2012-06-18
WGET a list of urls to a particular folder on desktop via command line?

So I have a list of url I want to wget. They are all different domains mostly. 

I want to go to the terminal and wget them all into a folder on my desktop

Let's say the folder is called Arlington

Can you write the commandline for me to accomplish this? I want all the images and videos etc from the list of urls.

---

### Post by gardnan on 2012-06-18
cd Arlington
wget -i /path/to/inputfile

---

### Post by josephmills on 2012-06-18
```
wget -r -i ~/Desktop/somefile --output-document=$HOME/Desktop/somedir -erobots=off

```

---

### Post by bostoncab on 2012-06-18
Where do I input the list of urls in that command line?

---

### Post by gardnan on 2012-06-18
> **bostoncab said:**
> Where do I input the list of urls in that command line?

I am not sure exactly what you are referring to, but in the two commands above, the file specified after the -i option is the one containing the list of urls.

---

### Post by matt_symes on 2012-06-18
Hi

This is a variation on the way Joseph poosted. It does not get the urls from a file but from the command line.

It will get  all the files from the bbc.co.uk and then move onto embeddedlinux.org.cn

Don't try this example as the bbc site is huge :)

```
wget [COLOR="Sienna"]-P ~/Desktop/tmp[/COLOR] [COLOR="Green"]-o log.txt[/COLOR] [COLOR="Red"]-r[/COLOR] [COLOR="blue"]-i <(echo -e "http://www.bbc.co.uk \n http://www.embeddedlinux.org.cn/")[/COLOR]
```

I have colour coded the sections.

[COLOR="Sienna"]The path prefix to download to. I.E download path[/COLOR] 
[COLOR="Green"]The log file to log in. Using the above, the log file be created in the pwd[/COLOR] 
[COLOR="Red"]Flag to get all files from the site (Recurse)[/COLOR] 
[COLOR="blue"]A list of urls to download seperated by \n.[/COLOR]

Kind regards

---

### Post by bostoncab on 2012-06-19
> **gardnan said:**
> I am not sure exactly what you are referring to, but in the two commands above, the file specified after the -i option is the one containing the list of urls.

so I should put all the urls in a text file and replace somefile with nameoffile.txt and run that in the command line as is.

I like the idea of wget a huge website but I am looking for specific content and I already know how to harvest the top 1,000 results for specific keywords so... I am just looking to pull down those 1,000 pages specifically.

---

