---
title: "Using python for a straddling Checkerboard Cipher?"
date: 2011-03-01
forum: Programming Talk
---

### Post by Moeie586 on 2011-03-01
I have to implement a cipher for the straddling checkerboard using  Python. For what I have, I don't know if I am on the right track and  just made a few errors, or if I am just completely misunderstanding how  to execute this..
 
but here were the instructions:
 [I]-You are to ask a user running  the program to enter plaintext and strip it of all non-letters. Your  program needs to print to the screen the stripped version of plaintext  for both testing and grading purposes. 
 
For part 1, you are also to generate a checkerboard (i.e. key). A checkerboard should be implemented in the following manner:
 
-set up a function that returns a string that consists of the following substrings:
      substring 1 is high frequency letters with 2 blanks ('estoniar   '), followed by substring 2 which is all the other letters in the  alphabet with 2 additional characters . and /
 
-characters in each substring are randomly scrambled so that each run of this function
 
-returns a different overall string, e.g. 'a stoin  ergqpymzc.jxhvuwfldbk/',  'inoretas  mfzdckbyq/jgulp.whxv', 'asn tiore   p/dhfucvbgz.wkmyjqlx', etc.
 
 
Then, in another function, split the resulting string into 3 substrings  of length 10 and find blank positions in substring 1. For testing and  grading purposes, this function is to print to the screen the resulting  three substrings, as well as index values of both blanks. To find the  second blank, use the function rfind (seraches backward in a string).[/I]
 
 
 [B]AND HERE IS MY CODE THAT I HAVE SO FAR:


def checkerboard(plaintext):
    string1="estoniar  "
    string2="bcdfghjklmpquvwxyz./"
    plainstripped=''
    for ch in plaintext:
        if ch.isalpha():
            plainstripped=plainstripped+ch
            plainstripped=plainstripped.lower()
            ciphertext=' '
            for ch in plainstripped:
                if ch in string1:
                    idx=string1.index('ch')
                    ciphertext=ciphertext+idx
                elif ch in string2:
                    idx2=string2.index('ch')
                    ciphertext=ciphertext+idx2
                else:
                    idx3=string3.index('ch')
                    ciphertext=ciphertext+idx3
                    return ciphertext
    

any help or hints towards the right direction would be great..thanks a lot!
[/B]

---

### Post by Tony Flury on 2011-03-02
Try posting your code in CODE tags like this : 

```

def someFunc( arg1, arg2, arg3)
    # Some code
    print arg1 + arg2+arg3

```

As you should know python is indentation sensitive, and it is a tough job (and potentially impossible) to reconstruct the idented python script when all the indentation is stripped away.

A couple of things that i can spot : 
1) Is this meant to be your first function - that generates a random checkerboard key ? if so it does not look randomised to me - and i don't think at this stage you want to do anything with the plain text ?
2) your last check looks at string3 - what is string3 - you don't define it anywhere.
3) I assume this is homework - at least you made an effort to code something - so thank you for that.

---

