---
title: "Letter-phonenumber conversion"
date: 2007-09-01
forum: Programming Talk
---

### Post by rachet on 2007-09-01
I recently joined the university and in one of the subjects ("computer and program design) an assignment due 5th Sept had already been given to the students 2 months ago. No matter how hard I work I won't be able 2 complete the assignment in time and I would then have to do foundations in programming for half a year in order to continue. I know its not right to be greatly aided in an assignment but this is a difference between me taking a whole year doing foundation and me continuing with the rest of the class. I will do private tutoring in c-programming this long holidays and definitely catch up.Please lend me a helping hand in the following program. Any help will be greatly apreciated.

We are to write a program in 'C' that would translate a string of 7 or 10 character words into its corresponding number according to the layout of a phone pad. We were to write 3 functions as follows;

1. Write a function to check phone numbers where this function takes in a string representing the dictionary word and returns a string representing the appropriate phone number. The phone number should be set to the "empty" string if the word does not form a phone number.
2. Write another function that takes in a single character and returns the associated phone digit (as a character). For example, the character 'A' would return '2'. For this program, you are to ignore the case of the character (thus 'g' and 'G' would return 4. If the character does not appear as a number on the phone, your function is to return '0' to signal this fact.
3. Write the main function that should open the input file containing the words and the output file to store the output. It should then read every word from the input file (one at a time) and as it reads each word, call the function to check the phone number to see if it is convertible. If the word forms a valid phone number of 7 or 10 letters, print this information into the output file. Finally, print the percentage of valid phone numbers that can be derived (either to the output file or to the screen) and then close the output and input files.


Specifics:
-You must search through all the words in the stored in a file, checking to see which ones are valid phone numbers.
-You should use the strlen function to determine the length of each word.
-Each word is on a separate line of the file. You are required to use the fgets function to read each word (line).
-Your program should write (save) each word that corresponds to a number (followed by its number) into a file.
-You must count how many 7 or 10 letter words are in the file and how many of these words translate into phone numbers. You should print the percentage (to 1 decimal place) at the end of your program, either into a file or to the screen.

An example of the last couple of lines of you’re the output would be:
...
word yesteryear is the phone number 937-837-9327
word yipping is the phone number 947-7464
word yttrium is the phone number 988-7486
96.8 percent of the 7/10 letter words that were translatable into phone numbers

-Your main function should return 0 upon completion.

---

### Post by aks44 on 2007-09-01
> **rachet said:**
> this is a difference between me taking a whole year doing foundation and me continuing with the rest of the class.

No matter the reason, we won't do your own homework. Moreover, all you need to do has been written down by your professor in the assignment, every single step is there.


I personally find your post pretty insulting, as it shows the real value that these forums and their community have in your eyes.


However, if you're really struggling with something **precise** (eg. a few lines of code not working as expected, a concept you don't understand, ...) then post the incriminated code portion and explain the problem. ***We'll be glad to help, if you're willing to show us that you can work by yourself.*** It's ok to ask for some help, but it's not to ask people to do all the work for you.


> **rachet said:**
> Any help will be greatly apreciated.

Since I'm in a good mood, I'll give away some code anyway, that will help you starting your program:

```
void main(void)
{
  /* insert the rest of the code here */
}
```

Warning, I deliberately put a trick in the above code (people please don't correct it, the OP should have learned that already).

---

### Post by CptPicard on 2007-09-01
Seriously, if you're not able to do that by Sep. 5, you NEED to do the foundations. You can't just bullshit your way through assignments, it'll catch up with you.

Your assignment is doable in a few hours max with knowledge of the proper prerequisites.

EDIT: I started doing this as an excercise in Scheme as I am getting rusty in the basics.. and there is a part of the assignment I don't understand. If there is a mapping between numbers and letters according to the phone pad, is it possible not to have a valid phone number? There is probably something I am not aware of in terms what what is an acceptable phone number...

EDIT 2: Ok, just an example of simple this really is. Can't be bothered to write it all the way with I/O and all.. hope it's unhelpful :p

```



(define phonepad '((#\A . 1) (#\B . 2) (#\C . 3) (#\D . 4)))
(define dictionary '("ABC" "CDE" "CDA"))



(define (map_list f l)
   (if (null? l)
      '()
       (cons (f (car l)) (map_list f (cdr l)))))


(define (lettertodigit letter)
	(let ((result_pair (assoc letter phonepad)))
		(if (pair? result_pair)
		    (cdr result_pair)
		    #f)))


(define (stringtonumber word)
	(if (string? word)
	    (let ((result (map_list lettertodigit (string->list word))))
	    	 (if (member #f result)
			#f
			(list->string (map_list integer->char result))))))


(define (makenumbers)
	(delete #f (map_list stringtonumber dictionary)))

(makenumbers)

```

:)

---

### Post by peabody on 2007-09-01
> **CptPicard said:**
> 
EDIT: I started doing this as an excercise in Scheme as I am getting rusty in the basics.. and there is a part of the assignment I don't understand. If there is a mapping between numbers and letters according to the phone pad, is it possible not to have a valid phone number? There is probably something I am not aware of in terms what what is an acceptable phone number...


Old telephone pads didn't have all the letters of the alphabet.  They were missing the letter Q and something else if I'm not mistaken.  Modern cell phones have everything I believe.  I think it had something to do with the fact that they only wanted three letters per number and 26 didn't divide evenly into 8 digits (1 has no letters since it was a digit used for long distance and hence would make it hard to have telephone numbers that started with those letters, and 0 had no letters for whatever reason).

To the original poster: I sympathize with you much more than the second poster, but that individual is right, if somewhat harsh.  If you want help, you're going to need to ask more specific questions, such as "How do I get input from the user?", "How can I open a file?", "How can I map a letter to a number?", etc.  We can help you with that.  It's best to stick to those types of questions if asking for help on homework.  Some people are very adamant about not helping people with homework.  Saying as much already has likely ostracized  you here.

The most important thing is to not panic.  Stay calm, build the program in small steps.  If you don't understand how something works in C, build a small test program to test how that language feature is supposed to work.

Are you a transfer student perchance?

---

