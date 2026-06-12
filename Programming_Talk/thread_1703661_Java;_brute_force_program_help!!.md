---
title: "Java; brute force program help!!"
date: 2011-03-09
forum: Programming Talk
---

### Post by noblerabbit on 2011-03-09
Hey all!

This is my last resort after having tried for days to figure it out.

An assignment asked me to create a program that would crack, with brute force, a password hashed in SHA1 (assuming it isnt salted, etc. its just basic)

I found an algorithm for generating strings of lower case letters and worked with it to check for matches to given SHA1 hashes.

What the program does, is takes in a SHA1 hash, and tries combinations of letters, hashing them, and matching them with the original.

Heres my code:

```

import java.io.UnsupportedEncodingException;
import java.security.NoSuchAlgorithmException;
import java.util.Arrays;
import java.util.Scanner;

public class BruteForce {

    // a variable to remember the start time,  use the following methods
    long timer = 0;

    void timeStart() {
        timer = System.currentTimeMillis();
    }

    void timeStop(String s) {
        timer = System.currentTimeMillis() - timer;
        if (s.equals("showMs") || s.equals("")) {
            System.out.println("Time taken is " + timer + "  milliseconds");
        } else if (s.equals("showSec")) {
            System.out.println("Time taken is " + timer / 1000 + " seconds");
        } else if (s.equals("showMin")) {
            System.out.println("Time taken is " + timer / 60000 + " munites and " + (timer % 60000) / 1000 + " seconds");
        }
    }

    public static void main(String[] args) throws NoSuchAlgorithmException, UnsupportedEncodingException {

        //user enters SHA1 hash string
        Scanner scanner = new Scanner(System.in);
        System.out.println("enter SHA1 hash string: ");
        String password = scanner.nextLine();

        //cracker only uses lower case alpha letters
        char[] charset = "abcdefghijklmnopqrstuvwxyz".toCharArray();
        //instantiate bruteforce object
        BruteForce bf = new BruteForce(charset, 1);
        //start the timer
        bf.timeStart();

        String hashAttempt = "";
        String attempt = bf.toString();
        while (true) {
            if (hashAttempt.equals(password)) {
                bf.timeStop("showSec");
                System.out.println("Password Found: " + attempt);
                break;
            }
            attempt = bf.toString();
            hashAttempt = Conversion.SHA1(attempt);
            //System.out.println("Tried: " + attempt);
            bf.increment();
        }
    }
    private char[] cs; // Character Set
    private char[] cg; // Current Guess

    public BruteForce(char[] characterSet, int guessLength) {
        cs = characterSet;
        cg = new char[guessLength];
        Arrays.fill(cg, cs[0]);
    }

    public void increment() {
        int index = cg.length - 1;
        while (index >= 0) {
            if (cg[index] == cs[cs.length - 1]) {
                if (index == 0) {
                    cg = new char[cg.length + 1];
                    Arrays.fill(cg, cs[0]);
                    break;
                } else {
                    cg[index] = cs[0];
                    index--;
                }
            } else {
                cg[index] = cs[Arrays.binarySearch(cs, cg[index]) + 1];
                break;
            }
        }
    }

    public String toString() {
        return String.valueOf(cg);
    }
}

```

I need it to also use numbers 0-9 in addition to lowercase letters but I cannot for the life of me understand how to do it :(
Is it just an easy fix or is it a case of having to rework the whole algorithm to work with a character set including numbers???

Thanks ever so much in advance for any insight!

---

### Post by unknownPoster on 2011-03-09
I've done this before. 

I'd create my own array of possible characters. Then iterate through that array to build possible password strings.

---

### Post by noblerabbit on 2011-03-09
> **unknownPoster said:**
> I've done this before. 

I'd create my own array of possible characters. Then iterate through that array to build possible password strings.

i tried adding the 0-9 numbers to the character set array but it throws an error:
```

Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: -36
        at bruteforce.BruteForce.increment(BruteForce.java:80)
        at bruteforce.BruteForce.main(BruteForce.java:55)
Java Result: 1

```

---

### Post by Some Penguin on 2011-03-10
I find it very odd that one would use binary search anywhere when attempting to force SHA-1, instead of iterating through all characters.

---

### Post by noblerabbit on 2011-03-10
Figured it out with help from someone.

I was just adding the numbers to the end of the array, but binarysearch needs the array to be sorted, so sticking the numbers in at the beginning, like so:

```

        char[] charset = {'0', '1', '2', '3', '4', '5', '6', '7', '8', '9', 'a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z'};

```

did the trick!:popcorn:

---

### Post by unknownPoster on 2011-03-10
> **Some Penguin said:**
> I find it very odd that one would use binary search anywhere when attempting to force SHA-1, instead of iterating through all characters.

Same here. I even suggested that the iteration be done, but I guess it was ignored.

---

