---
title: "[BASH] Calculating a Factorial &quot;Incorrect Input Error&quot;"
date: 2016-12-13
forum: Programming Talk
---

### Post by m-t-garcia1987 on 2016-12-13
I have some code that I am using to calculate a factorial in bash.

I am having a problem with a certain range of numbers 6-9 and I'm not sure why.

Here is the code that I am using:

```

printf "Please enter the number between 0-52 to find the factorial of.\n"
  while printf "Input Number: "; read input #Check for non-float number.
  do
    if [[ $input =~ ^[0-9]+$ && $input < 53 ]]; then #If correct input, then
      export number=$input
      nFact=1;
      while [ $input -ge 1 ]; do
        nFact=$(bc <<< "$nFact * $input");
        let input--
      done
      printf "Factorial of $number is : $nFact"
      break;
    else
      printf "\nIncorrect input. Enter a non-float number between 0-52.\n\n";
    fi
  done

```

I suspect (I'm almost positive) that the error is on line 4 as 6-9 are all above the first number in the set max of 53.

Here is a screen shot of the output I am getting (obviously the output is what I set for input out of range)
[ATTACH=CONFIG]272699[/ATTACH]

Edit: I figured out what was wrong. On line 4, I used the symbol "<" rather than "-lt". I changed it to "-lt" and it works fine now.

---

