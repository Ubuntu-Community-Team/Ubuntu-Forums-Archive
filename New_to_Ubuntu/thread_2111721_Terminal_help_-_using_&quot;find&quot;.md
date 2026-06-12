---
title: "Terminal help - using &quot;find&quot;"
date: 2013-02-02
forum: New to Ubuntu
---

### Post by AwaitingUserInput on 2013-02-02
I would like to recursively scan a directory for any files larger than 2 GB, and have the computer list their path and file size.

So far I did:
```
find -size 2G 
```
which looks like it MAY have worked, as it lists a few large files, but oddly, many of the results are under 2GB. There are some that are as small as 1.2 GB. Why is that?

Also, how can I get it to include the file size as part of the output whet I use the find command?

---

### Post by sisco311 on 2013-02-02
Try:
```
find ./ -size +2G -printf '%s bytes\t%p\n'
```
See:

[http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

---

### Post by sisco311 on 2013-02-02
Hmmm, it seems that find doesn't provide a way to display the size in GB, so you have to run something like:
```
while IFS=' ' read -r -d '' size file
do
    printf '%.2fG\t%s\n' $(bc <<< "scale=2; $size/(1024*1024*1024)") "$file"
done< <(find ./ -size +2G -printf '%s %p\0')

```in order to print the sizes in GB

---

### Post by AwaitingUserInput on 2013-02-02
> **sisco311 said:**
> Hmmm, it seems that find doesn't provide a way to display the size in GB, so you have to run something like:
```
while IFS=' ' read -r -d '' size file
do
    printf '%.2fG\t%s\n' $(bc <<< "scale=2; $size/(1024*1024*1024)") "$file"
done< <(find ./ -size +2G -printf '%s %p\0')

```in order to print the sizes in GB

Thanks, but I think this is way over my head at this point. Is that a bash script? Would it need to be saved in a *.s file and executed?

I'm a long way off before I start messing with scripting, unfortunately.

---

### Post by steeldriver on 2013-02-02
here's a somewhat simpler option - the output isn't formatted as nicely as sisco311's version but the basic info is there

```
find ./ -size +2G -exec ls -lh {} +
```or you could just do

```
$ find ./ -size +2G -ls
```if you don't mind sizes in plain bytes

---

### Post by sisco311 on 2013-02-02
> **AwaitingUserInput said:**
> Thanks, but I think this is way over my head at this point. Is that a bash script? Would it need to be saved in a *.s file and executed?

I'm a long way off before I start messing with scripting, unfortunately.

It's a compound command. :)

You can simply copy and past it in your terminal in order to run it. 

> **steeldriver said:**
> here's a somewhat simpler option


Thanks!

> **steeldriver said:**
> 
the output isn't formatted as nicely as sisco311's version but the basic info is there


I was trying to mimic the output format of the du command, instead of using it :redface: :
```
find ./ -type f -size +2G -exec du -h {} +
```

---

### Post by AwaitingUserInput on 2013-02-02
Thanks, guys! I did it both ways and yes, Sisco's output is prettier, and I got to learn about the -exec option in different commands. Thanks for the help!

---

### Post by andrew.46 on 2013-02-03
Mind you the answer can be found quite close to home:

[https://help.ubuntu.com/community/find#Acting_On_The_files](https://help.ubuntu.com/community/find#Acting_On_The_files)

which is a small variation on the OP's request. Some good stuff in the Ubuntu wiki :)

---

