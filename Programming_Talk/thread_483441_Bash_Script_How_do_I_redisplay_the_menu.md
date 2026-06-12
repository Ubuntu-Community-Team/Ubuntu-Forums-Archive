---
title: "Bash Script: How do I redisplay the menu??"
date: 2007-06-24
forum: Programming Talk
---

### Post by KrazyPenguin on 2007-06-24
Yes the while loop worked:


set -- option1 option2 option3

while [ 1 ]; do

select opt; do
   if[ "$opt" = option1]; then
        echo "do these commands"
   elif [ "$opt" = option2]; then 
        echo "do these commands instead"
   elif [ "$opt' = option3] then
       echo "bye!!!"
       exit
    else
       clear
       echo "Wrong Option"
      [COMMAND TO REDISPLAY MENU???] 
      break    
fi
done
done

So I needed to use "break" to break the first loop and set up a "while" loop to display the menu again.
Easy now that I think about it.  New to scripting.
Thanks,
;-)

---

### Post by raja on 2007-06-24
A while loop should do the job. 
```

while [i dont have the right option]; do
      (your code)
done
```
  
Something like that?

---

