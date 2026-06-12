---
title: "Basic Perl script - Noob question"
date: 2006-10-16
forum: Programming Talk
---

### Post by richardhr on 2006-10-16
Hi - Only just started my first perl program to download a load of pictures from my friends web site, there are over 500 images up there in one directory with sequential numbers.

I thought I could try and write a perl program to wget them the following downloads a single image (sample url):

```
wget http://www.tomwedding.com/1.jpg
```

This contacted the web site and downloaded my image.

SO I thought the following would work downloading a whole load of them:
```
#/usr/bin/perl

$i=1

while ($i<536){
 'wget 
http://www.tomwedding.com/$i.jpg';
i++;
}
```

but when I execute this i get the following error

```
./perlScript: line 3: =1: command not found
./perlScript: line 5: syntax error near unexpected token `{'
./perlScript: line 5: `while ($i<536){'
```

Can someone please point me in the right direction, I would be really greatful.

Thanks

I'm running:
Ubuntu 6.06 LTS - the Dapper Drake
This is perl, v5.8.7 built for i486-linux-gnu-thread-multi

---

### Post by girishv on 2006-10-16
Hi,

check the code in line number 8, it should read $i++ (not just i++), and you have to close the statement at line 2 with semi colon. First line should be #!, ok here is the full program
----------------------------------------------------------------------
#!/usr/bin/perl

$i=1;

while ($i<536){
 'wget http://www.tomwedding.com/$i.jpg';
$i++;
}
-------------------------------------------------------------------------

Instead of the above approach, it may be good to put all the links to images in a single file and get it through wget as
wget -i images.txt
This avoids making the wget resolve the ip address for each image.

Girish

---

### Post by richardhr on 2006-10-16
Thanks Girish

I used the file option - much cleaner.

Thanks for your time :-)

---

### Post by tenn on 2006-10-16
You could just use a firefox extension.

---

### Post by Woei on 2006-10-16
Or use the shell: 
```

for i in `seq 1 500`; do wget http://some.site/some_dir/$i.jpg; done

```

---

