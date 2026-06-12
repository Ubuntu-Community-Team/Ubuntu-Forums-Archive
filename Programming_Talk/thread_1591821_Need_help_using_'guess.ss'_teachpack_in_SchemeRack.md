---
title: "Need help using 'guess.ss' teachpack in Scheme/Racket"
date: 2010-10-09
forum: Programming Talk
---

### Post by NayJ on 2010-10-09
I was wondering if anyone knew how to use the 'guess.ss' teachpack found in DrRacket/Scheme? I ask because in my CS class, we're given word problems, that ask us to create a function, and sometimes an answer to run in scheme. Having said that this is my problem:
 
 
>   
Develop the function [COLOR=red]check-guess.[/COLOR] It consumes two numbers, [COLOR=red]guess [/COLOR]and [COLOR=red]target.[/COLOR] Depending on how guess relates to target, the function produces one of the following three answers: '**TooSmall**, '**Perfect**, or **'TooLarge.**
 
 
The function implements one part of a two-player number guessing game. One player picks a random number between 0 and 99999. The other player's goal is to determine this number, called target, with the least number of guesses. To each guess, the first player responds with one of the three responses that check-guess implements.
 
The function 'check-guess' and the teachpack [COLOR=red]gu[/COLOR][COLOR=red]ess.ss[/COLOR] implement the first player. The teachpack picks the random number, pops up a window in which the second player can choose digits, and hands over the guess and the target to check-guess. To play the game, set the teachpack to guess.ss using the Language|Set teachpack option. Then evaluate the expression 
[COLOR=royalblue] [/COLOR]
[COLOR=blue](guess-with-guicheck-guess)[/COLOR]
 
after check-guess has been thoroughly tested.


---

### Post by PC-XT on 2010-10-10
To load a teachpack, in the menu:
Language->Add Teachpack

About the teachpack:
[http://docs.racket-lang.org/teachpack/guess.html](http://docs.racket-lang.org/teachpack/guess.html)

---

### Post by NayJ on 2010-10-10
Alright so i was able to create a condition for check-guess giving me 'TooSmall, and 'TooLarge for answer when i got the second window to pop up, i just can't figure out how to make a function for 'Perfect. This is my code so far:
 
> (define (check-guess g t)
(cond
((> g 0) 'TooLarge)
((< g 99999)'TooSmall))
 
I'm also trying to figure out how to call the following program:
 
> ;;5.1.1
;;Formulating examples for the greeting "How Are You?" 
(define (reply s)
(cond
[(symbol=? 'HowAreYou?) 'Well]
[(symbol=? 'HowAreyou?) 'Couldbebetter]))
 
 
[COLOR=navy]Nevermind i was able to figure it out though another source[/COLOR]

---

