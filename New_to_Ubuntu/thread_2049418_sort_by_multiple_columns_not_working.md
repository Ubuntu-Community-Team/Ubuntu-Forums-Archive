---
title: "sort by multiple columns not working"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by fstriley on 2012-08-28
I know you don't believe me, that sort is not working, but here's the situation: I have the attached file tmp1.txt. I run this command:

$ sort -t',' -k1 -k2 -k9g -k7g -k8g -k3g -k4g -k12g -k10g -k11g -k5g -k6g -otmp2.txt tmp1.txt

the output tmp2.txt is attached. It seems to have gotten the -k1 -k2 correct. Columns 9 and 7 are not different, but then it should sort by column 8. It does not.

All help appreciated.

---

### Post by Miljet on 2012-08-28
I'm not sure just what you are expecting, but it appears that sort is doing exactly what it is supposed to do.

Sort normally begins at the beginning (left) of the line and continues to the right until it encounters a difference. Once a difference is encountered, it sorts the difference and ignores the rest of the line.

The (key) argument causes sort to begin somewhere other than the beginning of the line. And optionally, a second (key) argument stops the sort before the end of the line.

Depending on what you are trying to accomplish, you might possibly achieve your goal by piping the output of sort into a second sort operation.

---

### Post by fstriley on 2012-08-28
Thanks so much for the quick response, Miljet. As usual, I expected it to do what I meant, not what I said :-)

It's been a while and i had forgotten about the key ending. I changed my sort to:

$ sort -t, -k1,2 -k9,9g -k7,7g -k8,8g -k3,4g -k12,12g -k10,10g -k11,11g -k5,6g -otmp2.txt tmp1.txt

and now I get what I wanted.

Thanks for the reminder !

---

