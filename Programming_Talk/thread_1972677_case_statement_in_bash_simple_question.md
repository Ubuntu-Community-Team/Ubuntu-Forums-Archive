---
title: "case statement in bash simple question"
date: 2012-05-03
forum: Programming Talk
---

### Post by Alphamonkey on 2012-05-03
Hi, I am trying to write a simple case statement but I am having problems getting it to work.

What i want is to do a range of number in the case statement. This is for a lab for one of the classes I am taking. We are supposed to do for 90-100 grade = A 80-89 = B and so on. 

What I have so far is. 

```

#uses a case statement to determine grade corresponding to numerical score
#
#
clear
echo -n "enter numerical test score:"
read num_test_score             # take user input

case $num_test_score in         # start case statement
        9?)echo "A" ;;      #if 90-99 output a
        8?)echo "B" ;;      #same but for 80's
        7?)echo "C" ;;      #70's
        6?)echo "D" ;;      #60's
        100)echo "A" ;;     #100
        [0-9])echo "F" ;;         #0-9
        1?) echo "F" ;;     #10's
        2?) echo "F" ;;        #20's
        3?) echo "F" ;;      #30's
        4?) echo "F" ;;     #40's
        5?) echo "F" ;;     #50's
        *)echo "Please enter a valid value" #all other values so 100 and above
esac    #End case


```
It works, but I want to consolidate the last few statements for basically 0-59.

I thought I could do [0-59]) but it did not work. Could anyone please let me know how to do multiple values like that. Thanks.

---

### Post by papibe on 2012-05-03
Hi Alphamonkey.

For a 2 digit number ***string*** from 10 to 59 you could use expression:
```
[1-5][0-9]) echo "F" ;;
```
Hope that helps.
Regards.

---

### Post by Vaphell on 2012-05-03
regular expressions don't know the concept of numbers, it's all about sequences of characters. 0-9 works because it's the range of chars, just like a-z or A-Z.

[0-9]|[0-5][0-9]) should consume anything in 0-59 range (0-9 or 0-5,0-9), i used 0-5 assuming that 09 is a valid entry, if not then 1-5

```
$ for x in 9 09 33 66 100; do case $x in [0-9]|[0-5][0-9]) echo $x matches;; esac; done
9 matches
09 matches
33 matches
```

---

### Post by SeijiSensei on 2012-05-03
The construct "*)" is a wildcard or default match which you can use at the bottom of a "case" list to match any residual cases.  Look at the contents of a startup script in /etc/init.d for some examples.

---

