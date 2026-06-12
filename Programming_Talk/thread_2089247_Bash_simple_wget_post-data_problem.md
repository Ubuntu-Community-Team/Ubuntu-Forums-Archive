---
title: "Bash: simple wget post-data problem"
date: 2012-11-28
forum: Programming Talk
---

### Post by kpuz on 2012-11-28
Hi,
I am trying 'to retrieve a webpage that requires my email and password to scrape some personal data. Last night, I used the following commands to successfully get the the page:
Code:
```

wget --save-cookies ./cookies.txt --delete-after --post-data 'email=me@gmail.com&password=mypassword' https://www.speakout7eleven.ca/login
wget --load-cookies ./cookies.txt https://www.speakout7eleven.ca/my-account/speakout-profile
```

The very first time I tried this command sequence, I was able to use the second wget command to load cookies and download the webpage.  However, it no longer works and I'm completely puzzled over why.  If I remove the --post-data part of the command, I am able to get the first page (/login) to be downloaded, however, with the --post-data part the page loads as 0kb.  I don't know what I'm doing wrong.  Any help?

---

