---
title: "character output in php"
date: 2009-10-14
forum: Programming Talk
---

### Post by panicy on 2009-10-14
A friend recently asked me for help with a (seemingly) small program.  The request is simple, but after working on it off and on for a couple of days Im stuck.  Im not sure if I have just began to over think the problem, or if it is truly deeper then I originally thought.  The request is this....  He needs the output of a 6 charactor number that has 2 options for each character within the number.  So for example thinking of it in binary with a six charactor number and two options for each charactor you are talking about a 64 number output (with ones and zeros as the options, 2^6), 111111, 111110, 111101, etc.  I know that I need a loop within it where i=0; i<2; i++ to keep each digit within 0 or 1.  But Im not sure of how to tell it in php to make it 6 digits long (an only 6 digits long) and to not reuse the ones that its already created.  :confused:  

I've been trying to do this in php to give him a web interface where eventually he could enter the number of digits and the possibilities for each character, but help in any programming language would be greatly appreciated. Sorry for the novel...

Thanks in advance!!

---

### Post by Can+~ on 2009-10-14
[PHP]
for ($i=0; $i<pow(2,$n); $i++)
    printf("%b", $i)[/PHP]

Read: [http://us3.php.net/manual/en/function.sprintf.php](http://us3.php.net/manual/en/function.sprintf.php)

000 = 0
001 = 1
010 = 2
011 = 3
100 = 4
101 = 5
110 = 6
111 = 7

It's about taking the number from 0 to 2^n-1 and printing as binary.

---

