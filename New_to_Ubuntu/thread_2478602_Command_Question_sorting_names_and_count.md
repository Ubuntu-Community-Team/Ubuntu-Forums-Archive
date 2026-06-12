---
title: "Command Question: sorting names and count"
date: 2022-08-30
forum: New to Ubuntu
---

### Post by sogo-77 on 2022-08-30
I am so very new to this program and I hope someone can help me with this. 
So I have a file with data log and bunch of names. I just want to sort the name out & summarize how many times each name has. 
So the results should be:
Sssssss = 3
Ddddddd = 4
Ttyttyttttt = 5
Something like this. 
What's a perfect command for this? 
Thank you in advance.

---

### Post by The Cog on 2022-08-30
How about 
```
awk '{counts[$0]+=1}END{for (key in counts) {print key,"=",counts[key]}}' filename
```
You can pass this through sort to get alphabetic or numeric sorting:
```
awk '{counts[$0]+=1}END{for (key in counts) {print key,"=",counts[key]}}' filename | sort
awk '{counts[$0]+=1}END{for (key in counts) {print key,"=",counts[key]}}' filename | sort -g -k3 -t ' '
```

---

### Post by TheFu on 2022-08-30
> **sogo-77 said:**
> I am so very new to this program and I hope someone can help me with this. 


Ah ... I see the school semester has begun again.  There are 500 solutions.  Post what you have and we can provide ideals, but it is against forum rules to ask someone to solve your homework.

---

### Post by Impavidus on 2022-08-31
You didn't tell what the data file looks like. Is it one name per line? Look into the sort and uniq commands. Read the man pages and pick the appropriate options. Consider using a pipe. I think I've said more than enough.

---

