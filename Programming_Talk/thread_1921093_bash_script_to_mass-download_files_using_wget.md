---
title: "bash script to mass-download files using wget ?"
date: 2012-02-06
forum: Programming Talk
---

### Post by shevin on 2012-02-06
Hey guys

I need to download bunch of files everyday from a website,

the url would be either :
[https://mysite.com/uloaded/12100001/pdf](https://mysite.com/uloaded/12100001/pdf)
[https://mysite.com/uploaded/12100001/word](https://mysite.com/uploaded/12100001/word)


the number 12100001 increases everyday,
and each number may either be word or jpg

so i need to write a bash script to download every file from a range of numbers (let say 12100001 to 13100000), and try to download all the three possilbiities PDF , JPG and WORD for each number and download all of them


how could I write such a thing in bash or python or any other language?

---

### Post by Mosome on 2012-02-06
You could use bash in a loop along with wget.  Something like should work if you know the exact ranges:

for (( n = <start>; $n < $MAX; n++ )); do
    wget "address" -O file$n.jpg
    if !( [ -f "file$n.jpg" ] ); then
       exit
    fi
done

---

### Post by Lars Noodén on 2012-02-06
It's not too difficult to do in Perl either.  The module for fetching web pages is [LWP](http://search.cpan.org/~gaas/libwww-perl-6.03/lib/LWP.pm)

---

### Post by shevin on 2012-02-06
> **Mosome said:**
> You could use bash in a loop along with wget.  Something like should work if you know the exact ranges:

for (( n = <start>; $n < $MAX; n++ )); do
    wget "address" -O file$n.jpg
    if !( [ -f "file$n.jpg" ] ); then
       exit
    fi
done


could you please explain your code a lil bit for me?
shouldn't we put the file$n inside the "address" ? as far as I know -O in wget is for the output ...we need the script to automatically change and increment the address 
so for example we need to download all the files from address [https://mysite.com/uploaded/12100001](https://mysite.com/uploaded/12100001) to [https://mysite.com/uploaded/13100001](https://mysite.com/uploaded/13100001)


and another advanced question, what if the site requires login , could we give the username pass to wget to login and then download ?

---

### Post by emiller12345 on 2012-02-06
try this...
```
~$ COUNT=12100001; while [ $COUNT -le 13100001 ]; do wget "https://mysite.com/uploaded/$COUNT/word"; wget "https://mysite.com/uploaded/$COUNT/pdf"; wget "https://mysite.com/uploaded/$COUNT/jpg"; COUNT=$(($COUNT+1)); done
```You may want to add a couple of sleep commands so you don't overload the server

---

