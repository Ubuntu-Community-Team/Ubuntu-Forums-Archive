---
title: "Bash Conditional While Loop and Saving Variable"
date: 2016-11-28
forum: New to Ubuntu
---

### Post by m-t-garcia1987 on 2016-11-28
I am trying to run a script in bash that takes user input, checks if it is a valid integer and moves on if it is. 

This is what I have so far. 

```

while read input
do
  if [[ $input == ^-?[0-9]+$ ]]; then
    export multiplicand=$input
    break
  else
    printf "\n\nIncorrect input. Please enter whole positive or negative number: ";
  fi
done

```

This endlessly loops saying invalid input. Can someone give me a bit of guidance.

Edit: Answered my own question... changed "==" to "=~" and it worked fine.

---

### Post by TheFu on 2016-11-28
Please mark thread as "SOLVED" to help out the community.

---

