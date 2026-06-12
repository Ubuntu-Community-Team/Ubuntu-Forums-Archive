---
title: "Java String.equals()"
date: 2010-12-28
forum: Programming Talk
---

### Post by shababhsiddique on 2010-12-28
I am having trouble with the String.equals(String) function


well here is what i am doing.

origin is fetched from a vector which was filled up by reading a text file.

answer is from standard input. readline()


i have to match the two words and see if they are equal.

origin.equals(answer)



  boolean match=true;
  for (int index = 0; index < answer.length(); index++) {
                   if(answer.charAt(index)!=origin.charAt(index))
                   {
                       match=false;
                   }
                }
  System.out.println(match);
  System.out.println(answer.equals(origin));


match= true
but
answer.equals(origin)=false


what is wrong?

does the readline() add any /r or something at the end?

---

### Post by Some Penguin on 2010-12-28
Step through your code.

What does your code do if answer = "Blarg blarg" and origin = "Blarg"?  And what does it do if we switch those?

---

### Post by shababhsiddique on 2010-12-28
here is the vector construction

Vector<String>	respList = new Vector<String>();
        do
        {
           // String reader;
           
            i= fin.read();
            if(i>-1){
                
                if((char)i=='\n'){
                    respList.add(s);
                    s="";
                  //  System.out.println();
                }
                else
                {  
                 //   System.out.print((char)i);
                    s=s+(char)i;
                }
                
            }
            
        }while(i!=-1);

---

### Post by Some Penguin on 2010-12-28
One, use 'code' tags.  Two, there were obvious errors even in your first post that should be easily noticed if you use the pair of inputs I suggested.  Even simpler, use 'AB' and 'A'.

---

### Post by shababhsiddique on 2010-12-28
> **Some Penguin said:**
> Step through your code.

What does your code do if answer = "Blarg blarg" and origin = "Blarg"?  And what does it do if we switch those?


its still says false

---

### Post by Some Penguin on 2010-12-28
Not when origin is shorter than answer, it won't.  Your code will die with an exception.

---

### Post by shababhsiddique on 2010-12-28
```

boolean match=(answer.length()==origin.length());
               for (int index = 0; index < answer.length(); index++) {
               
                   if(answer.charAt(index)!=origin.charAt(index))
                   {
                       match=false;
                   }
                }

```

anyway i dont want to use this loop. I want to use answer.equals(origin)

---

### Post by shababhsiddique on 2010-12-28
> **Some Penguin said:**
> Step through your code.

What does your code do if answer = "Blarg blarg" and origin = "Blarg"?  And what does it do if we switch those?


I just noticed something when stepping through.
The length of answer is as expected but the length of origin is +1
perhaps a special character is added. 

How do i resize it?

---

### Post by shababhsiddique on 2010-12-28
from debug watches i see

answer contains "oracle"

origin contains "oracle\r"

---

### Post by schauerlich on 2010-12-28
Stop coding. Write down the algorithm in pseudocode. Follow it precisely by hand on the inputs Some Penguin has suggested. Once you figure out why it doesn't work, go back and fix your code.

---

### Post by shababhsiddique on 2010-12-28
> **Some Penguin said:**
> Not when origin is shorter than answer, it won't.  Your code will die with an exception.

yes it shall die with exception. Plz help me

---

### Post by Some Penguin on 2010-12-28
Instead of trying to use an input stream like that, directly, have a look at BufferedReader's readLine() to read... entire lines at a time.  And Vector is replaceable in many cases by ArrayList, since often you don't need the synchronization overhead of Vector.

---

### Post by shababhsiddique on 2010-12-28
Thanks all you guys. I am newbie in java so sorry to bother with so easy things.

Anyway problem is solved.

I wasnt expecting the lines include a carriage return \r 

This made the strings not equal.

---

