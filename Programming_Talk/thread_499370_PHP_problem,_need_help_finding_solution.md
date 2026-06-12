---
title: "PHP problem, need help finding solution"
date: 2007-07-12
forum: Programming Talk
---

### Post by nesh87 on 2007-07-12
Hey guys,
i have a project for uni where i have to code an ATM for a user using PHP-CLI. i have coded the whole program including, deposits, withdrawals, interest, balance screens. Everything is going well, however, for the withdrawal , i have to make sure that the user can only withdraw 50 or 20 or combination of both. I have no idea on how to code this. One idea i got is that i would check the withdrawal amount requested and divide it by 50 and then divide by 20, if both return a postive integer, then the program would complete the process. If one of them fails, i would check if at least one of them works. Im not sure this correct neither do i know how top put this in actual code. I am a newbie in PHP and most programming languages ;p..

any help from you guys is appreciated :D

---

### Post by Wybiral on 2007-07-12
Maybe I'm misunderstanding something here, but...

```

if($withdraw_total==20 || $withdraw_total==50 || $withdraw_total==70)
{
    // OK
}

```


EDIT:
Oh, nevermind... (forgot that they were probably accumulating)

---

### Post by scragar on 2007-07-12
```
$amount = 170;
$tmp = $amount%50;
if($tmp%20 == 0){
  // $amount can be found using only 20s and 50s.
}else{
  // amount cannot be goten using 20s and 50s only
};
```
% is used for modular division(finds the remainder of the division):
17%5 = 2
6%7 = 6
4%4 = 0

---

### Post by nesh87 on 2007-07-12
wow 2 replies that fast :D... now thats what i call a user-friendly community.. i love this community..
anyways thanks a lot guys for your replies.. i think the modular division will work..

IT kinda worked, but some numbers dont work correctly
for example if i enter 60, the program responds with the error however if i enter 110 i get the error even though 110 can be one 50 and three 20..

this is my code:
> 
($enteredOption == 3) {

		Print "\nEnter Amount to be withdrawn: $currency";

		$withdrawAmount = trim(fgets(STDIN));

		//check positive withdraw amount and enough funds in total balance		
		IF ($withdrawAmount > 0) {
			IF ($totalBalance >= $withdrawAmount) {
				$tmpwithdrawAmount = $withdrawAmount%50;

				IF ($tmpwithdrawAmount%20 == 0){

					$totalBalance = $totalBalance - $withdrawAmount;
					Print "\nYou have withdrawn $currency $withdrawAmount\n";
					Print "Your current balance is $currency $totalBalance\n \n";
					sleep(2);
				}ELSE {
					Print "Only $currency" ."50 and $currency" ."20 notes can be used";
				}

			} ELSE {

				Print "\nYou have insufficient funds\n";
				Print "Please try a lower amount: ";
				$withdrawAmount = trim(fgets(STDIN));
				Print "\nYou have withdrawn $currency $withdrawAmount\n";
				Print "Your current balance is $currency $totalBalance\\n";								
				sleep(2);
			}
		} ELSE {
			Print "Please enter a positive value: $currency";
			$withdrawAmount = trim(fgets(STDIN));
			sleep(2);
		}


---

### Post by aks44 on 2007-07-12
> **scragar said:**
> ```
$amount = 170;
$tmp = $amount%50;
if($tmp%20 == 0){
  // $amount can be found using only 20s and 50s.
}else{
  // amount cannot be goten using 20s and 50s only
};
```
% is used for modular division(finds the remainder of the division):
17%5 = 2
6%7 = 6
4%4 = 0

80 % 50 = 30
30 % 20 = 10

EDIT: nesh87's edit beat my post...

---

### Post by scragar on 2007-07-12
oops. this should work:

```

$amount = 60;
$tmp = amount % 100;//first we test agains 100.
if($tmp%20 == 0|| tmp%50 == 0){
//valid.
}else{
//invalid.
};
```

---

### Post by aks44 on 2007-07-12
> **scragar said:**
> oops. this should work:

```

$amount = 60;
$tmp = amount % 100;//first we test agains 100.
if($tmp%20 == 0|| tmp%50 == 0){
//valid.
}else{
//invalid.
};
```

70 % 100 = 70
70 % 50 = 20
70 % 20 = 10

still missing something ;)

---

### Post by nesh87 on 2007-07-12
> **scragar said:**
> oops. this should work:

```

$amount = 60;
$tmp = amount % 100;//first we test agains 100.
if($tmp%20 == 0|| tmp%50 == 0){
//valid.
}else{
//invalid.
};
```

This one did the job :D.. thanks a bunch... if you dont mind, can you tell me why u used % 100 first?

Edit: SPoke too soon ;p... if i try to withdraw 110 i get the error.. however 110 can be withdrawn using one 50 and 3 20s ...

---

### Post by scragar on 2007-07-12
I know, I can't seam to think of a way to ensure that strange values of them don't add up...

```
function check($amount){
  for($i = 0; $i < 4; $i++){
    if(($amount-(50*$i))%20 == 0)
      return true;
  };
  return false;
};
echo check(70)?"y":"n";
echo check(30)?"y":"n";
echo check(100)?"y":"n";
```
can anyone find any instances in which this fails?

---

### Post by aks44 on 2007-07-12
> **scragar said:**
> ```
function check($amount){
  for($i = 0; $i < 4; $i++){
    if(($amount-(50*$i))%20 == 0)
      return true;
  };
  return false;
};
echo check(70)?"y":"n";
echo check(30)?"y":"n";
echo check(100)?"y":"n";
```
can anyone find any instances in which this fails?

check(10) and check(30) return true :p

funny thread :popcorn:

EDIT: i'll help you a little: a one liner is all you need ;)

---

### Post by scragar on 2007-07-12
```
function check($amount){
  for($i = 0; $i < 4; $i++){
    if(50 * $i < $amount){
      if(($amount-(50*$i))%20 == 0)
        return true;
    };
  };
  return false;
};
```this function works for all tests between 10 and 300, so I can't see any problems with it.

---

### Post by destructchaos on 2007-07-12
instead of trying to figure out if yours works, i figured i throw in another option ... the recursive binary tree approach:
```

function check($amt) {
   if ($amt == 0)
      return true;
   else {
      if (amt < 0)
         return false;
      else
         return check(amt - 50) || check(amt - 20);
   }
}

```

---

### Post by scragar on 2007-07-12
> function check($amt) {
   if ($amt == 0)
      return true;
   else {
      if (amt < 0)
         return false;
      else
         return check(amt - 50) || check(amt - 20);
   }
}
you missed the $ on line 5, but that should work.

---

### Post by aks44 on 2007-07-12
> **scragar said:**
> ```
function check($amount){
  for($i = 0; $i < 4; $i++){
    if(50 * $i < $amount){
      if(($amount-(50*$i))%20 == 0)
        return true;
    };
  };
  return false;
};
```this function works for all tests between 10 and 300, so I can't see any problems with it.

check(50) returns false.

> **destructchaos said:**
> instead of trying to figure out if yours works, i figured i throw in another option ... the recursive binary tree approach:
```

function check($amt) {
   if ($amt == 0)
      return true;
   else {
      if (amt < 0)
         return false;
      else
         return check(amt - 50) || check(amt - 20);
   }
}

```

works fine, but unnecessary burden imho.

> **scragar said:**
> you missed the $ on line 5, but that should work.

two $ missing on line 8 too.

---

### Post by destructchaos on 2007-07-12
sorry, i've been writting java all day.

---

### Post by nesh87 on 2007-07-12
> **scragar said:**
> ```
function check($amount){
  for($i = 0; $i < 4; $i++){
    if(50 * $i < $amount){
      if(($amount-(50*$i))%20 == 0)
        return true;
    };
  };
  return false;
};
```this function works for all tests between 10 and 300, so I can't see any problems with it.

Im completely Lost here :D.... excuse my lack of experience.. anyhow, 50 for this function doesnt work, returns false.. this is what i did to test it:
[PHP]
function check($amount){
  for($i = 0; $i < 4; $i++){
    if(50 * $i < $amount){
      if(($amount-(50*$i))%20 == 0)
        return true;
    };
  };
  return false;
};

while (true) {
$withdraw = trim(fgets(STDIN));
if (check($withdraw) == true) {
Print "true";
} else {
Print "false";
}

}
[/PHP]

ill try the other function see if it works :D

---

### Post by aks44 on 2007-07-12
Now, who will find the simple, constant-time-3-comparisons-only one liner that solves the problem? :-({|=

:popcorn:

PS: sorry guys to let you find it, but it's so simple I just can't tell you ;)

---

### Post by destructchaos on 2007-07-12
horse puckey!  show us your magical one-liner; i gotta leave work soon and i want to see it before it do.

---

### Post by neoguy2012 on 2007-07-12
Is it this?

```

     function check($amt)
     {
     	if ($amt < 20 || $amt == 30 || $amt%10 != 0)
     	   return FALSE;
     	return TRUE;
     }

```

---

EDIT: I'm stupid:

```

     function check($amt)
     {
          return !($amt < 20 || $amt == 30 || $amt%10 != 0);
     }

```

---

### Post by aks44 on 2007-07-12
> **neoguy2012 said:**
> ```

     function check($amt)
     {
          return !($amt < 20 || $amt == 30 || $amt%10 != 0);
     }

```

GG :KS

I rather thought it the other way around, but it's the same anyway :

```
function check($amt)
{
  return (($amt >= 40) && ($amt % 10 == 0)) || ($amt == 20);
}
```

EDIT: removed my previous edit, looks like I'm tired :oops:

---

### Post by neoguy2012 on 2007-07-12
That was a good coding exercise.  If anyone wants to know why that code works... the modulus 10 thing is pretty straight forward since both 20 and 50 are divisible by 10.  The 10 and 30 thing is because the first two consecutive values (counting by tens) that work are 40 and 50.  Add 20 to 40 to get 60.  Add 20 to 50 to get 70.  Add 20 to 60 .... you get the point.  Sneaky problem if you ask me.  Let us know if you have any more fun problems like that.

---

### Post by aks44 on 2007-07-12
As a follow up... destructchaos' recursive solution is the best one if you need to know *which* notes you have to use:

```
function check($amt, &$notes20, &$notes50)
{
   if ($amt == 0)
      return true;
   elseif ($amt < 0)
      return false;
   elseif (check($amt - 50, $notes20, $notes50))
   {
      ++$notes50;
      return true;
   }
   elseif (check($amt - 20, $notes20, $notes50))
   {
      ++$notes20;
      return true;
   }
   else
      return false;
}

$amt = 330;
$n20 = 0;
$n50 = 0;
if (check($amt, $n20, $n50))
	echo "To withdraw $amt, you need $n50 notes of 50 and $n20 notes of 20.";
else
	echo "You can only withdraw notes of 20 and 50."
```

---

### Post by nesh87 on 2007-07-13
YES! it worked, thanks a lot guys,, im sure there will be more sneaky problems ill share them with you in the near future :D

---

### Post by destructchaos on 2007-07-13
> **aks44 said:**
> As a follow up... destructchaos' recursive solution is the best one if you need to know *which* notes you have to use:

```
function check($amt, &$notes20, &$notes50)
{
   if ($amt == 0)
      return true;
   elseif ($amt < 0)
      return false;
   elseif (check($amt - 50, $notes20, $notes50))
   {
      ++$notes50;
      return true;
   }
   elseif (check($amt - 20, $notes20, $notes50))
   {
      ++$notes20;
      return true;
   }
   else
      return false;
}

$amt = 330;
$n20 = 0;
$n50 = 0;
if (check($amt, $n20, $n50))
	echo "To withdraw $amt, you need $n50 notes of 50 and $n20 notes of 20.";
else
	echo "You can only withdraw notes of 20 and 50."
```


woot!  quick question though:

it's been a while since i've written anything in php, but if you declared your variables above the function call, wouldn't you not need to pass them to the function?  if the function accessed the global variables, you could save yourself a couple bytes of memory in the stack per function call.

---

### Post by aks44 on 2007-07-13
> **destructchaos said:**
> if you declared your variables above the function call, wouldn't you not need to pass them to the function?  if the function accessed the global variables, you could save yourself a couple bytes of memory in the stack per function call.

sure, but then the caller would HAVE TO use these global variables. I prefer flexibility and good encapsulation over saving a few bytes when the performance benefits are close to nothing. ;)

---

### Post by destructchaos on 2007-07-13
> **aks44 said:**
> I prefer flexibility and good encapsulation over saving a few bytes when the performance benefits are close to nothing. ;)

they may be close to nothing for the simple case of the demo project, but those bytes would add up quick if he was writing the back-end to a multi-million customer bank's ATM system.  i guess i prefer performance gains. no matter how small they each may be, they have a nasty habit of adding up to something noticeable.

---

### Post by aks44 on 2007-07-13
IMHO, premature optimization is the root of all evil...

The way I tend to program is:

1) Make it work
2) Make it maintenable
3) Make it useable (for the end-user, or other developpers if you're writing a library)
4) Profile, and fix the parts that are the less performant


Back to the point: "if he was writing the back-end to a multi-million customer bank's ATM system" it would be a multithreaded (maybe even clustered) server program, which anyway excludes the use of global variables :p

EDIT: or the code would be executed on a local ATM, where a few nanoseconds / 500 bytes of stack really don't matter.

---

### Post by destructchaos on 2007-07-13
i agree with your notiong on "premature" optimization and tend to follow a relatively similar design approach as you (i tend to invert steps 2 & 3); however, it always seems (to me atleast) that too many people skip step 4, so i try to consider the worst case performance senario while wirtting the code so that, if everything goes according to plan, there's not much to do for step 4.

back to the point: in the case of a multithreaded/clustered server program, the "global" variables would be local to the thread, so they aren't global in the C sense of the term.

to your edit: i had considered that but in the case of such a large system, it's a relatively safe assumption that the system designer would be a moron and not do that.  not to mention, that defeats the purpose of the thought experiment. :)

---

### Post by aks44 on 2007-07-13
> **destructchaos said:**
> it's a relatively safe assumption that the system designer would be a moron and not do that.

For your own security: never, ever say that again to a software architect, even if you're not targeting him directly :p Noone knows what could happen if he goes wild :)

More seriously, as you may know all those steps I mentionned are not as separated as I made them. I agree with you that good design can avoid performance problems beforehand (I learned that at my own expense ;)). But to me, making upfront micro optimizations that influence the overall design like you suggested are not worth the trouble, and can lead  to more problems than it solves IMHO.

I'd rather have the team spend a few days rewriting the relevant parts *once we are sure* that it won't ever matter (on a design level) rather than have them hunt for bugs during weeks (reentrancy problems in multithreaded environments are a plea to debug, when you don't know where to look at). Not to mention the stress factor that is associated with bug hunting, as opposed to a "routine code rewrite"...

EDIT: BTW, if the variables are thread-local, obviously you need some way to tell the function which instance it has to use. And honestly, function parameters are way easier to grasp than TLS... On the performance side I can't guess, it depends too much on the context (only a profiler can tell that) but again I tend to stay on the safe side...

---

### Post by destructchaos on 2007-07-13
> **aks44 said:**
> For your own security: never, ever say that again to a software architect, even if you're not targeting him directly :p Noone knows what could happen if he goes wild :)

i really only said that because i recently had to beat one over the head for doing something equally stupid.

back to the more serious section:  i believe we have reached a gentleman's disagreement.  i personally have never gotten myself into any major trouble (that i can remember off hand) by doing little tweaks like that, but as soon as i hit a major roadblock because of doing so, i'll probably revise my stance on the matter, though i do completely agree with you on the headaches associated with debugging multi-threaded apps.

to your edit:  not the way i was picturing it.  (aside: can php even do multi-threaded apps?)  i was picturing it like a normal web server where each php script is single threaded, but the server can instantiated as many threads of it as needed, thus the script thinks it's the only one and its global variables are such, but are really only global to that thread.

---

### Post by aks44 on 2007-07-13
> **destructchaos said:**
> to your edit:  not the way i was picturing it.  (aside: can php even do multi-threaded apps?)  i was picturing it like a normal web server where each php script is single threaded, but the server can instantiated as many threads of it as needed, thus the script thinks it's the only one and its global variables are such, but are really only global to that thread.

I have to agree that if a designer goes for a php web server in order to handle several millions of customers in a banking environment, he just deserves to be beaten to death :p

---

