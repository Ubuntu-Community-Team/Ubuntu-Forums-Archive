---
title: "list out the user whose home directory got more than 1MN file"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by Ericyue on 2012-06-28
hi, i want to dispay the user whose home directory has more than 1MB file. anyone know hoe to find that ? i have try the du and cut command but not sure how it actually works .. thanks in advance

---

### Post by papibe on 2012-06-29
Hi Ericyue.

Assuming that all users are under /home, you could get a list of the space each user is using with this command:
```
du -s /home/*
```
where:
[INDENT]'-s' is to print just one line for each directory with the sum of all space used
The results will be in kilos, so look for > 1024[/INDENT]

If you need a simple manual solution, you could sort the list an easily identify the users:
```
du -s /home/* | sort -n
```
where:
[INDENT]'-n' sorts the results using its numeric value.[/INDENT]

If you want to really just print the name of users you could use 'awk' to get access to the columns (this time assuming the name of the user's home matches his/her username):
```
cd /home
du -s * | awk '{if ($1 > 1024) print $2}'
```
where
[INDENT]'$1' reference the 1st column, i.e., the size.
'$2' is the name of the username.[/INDENT]

Alternatively, you may ask 'du' to print the disk usage in Mb:
```
cd /home
du -s -m * | awk '{if ($1 > 1) print $2}'
```

I hope that helps, or at least points you in the right direction.
Regards.

---

