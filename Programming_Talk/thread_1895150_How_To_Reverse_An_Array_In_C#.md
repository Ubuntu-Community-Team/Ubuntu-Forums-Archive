---
title: "How To Reverse An Array In C#"
date: 2011-12-14
forum: Programming Talk
---

### Post by Tarast on 2011-12-14
hi guys, i wrote this program that reads input from the user and stores it in array in correct oder, for example it would go 1, 2, 3, 4, 5, 6, etc i want to display the numbers in the reverse order they were entered. 
 
here is my code:
 
[FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]static[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]void[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] Main([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]string[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][] args)
{
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] count = 0;
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]string[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] countInput;
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][] number;
number = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]new[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][5];
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]for[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] (count = 0; count < 5; count++)
{
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Console[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].WriteLine([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Enter Number"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]);
countInput = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Console[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].ReadLine();
number[count] = [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].Parse(countInput);
}
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Console[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].WriteLine([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Your Entered Numbers Are:"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]);
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]foreach[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] ([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] yourNumbers [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]in[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] number)
{
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Console[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].WriteLine([/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Number: {0}"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2], yourNumbers);
}
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af][FONT=Consolas][SIZE=2][COLOR=#2b91af]Console[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2].ReadLine();
}
 
it works, now i just cant figure out how to display entered number in reverse, does anyone know ?
[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by Tarast on 2011-12-14
figured out never mind, array.reverse i had to use didnt know it existed lol

---

### Post by Petrolea on 2011-12-14
You could also make a for loop that would count backwards, which would be a better solution since not every programming language has a function for reversing array.

```

for(int i = array.Length - 1; i >= 0; i--)
{
    Console.Write(array[i] + " ");
}


```

---

### Post by cgroza on 2011-12-14
> **Petrolea said:**
> You could also make a for loop that would count backwards, which would be a better solution since not every programming language has a function for reversing array.

```

for(int i = array.Length - 1; i >= 0; i--)
{
    Console.Write(array[i] + " ");
}


```
Why reinvent a wheel in this case? Maybe only to build a more faster algorithm for a specific case.

---

### Post by Petrolea on 2011-12-15
> **cgroza said:**
> Why reinvent a wheel in this case? Maybe only to build a more faster algorithm for a specific case.
In this case my reply didn't help at all.

But I replied just to show OP that there's another way of doing it and that it is way more portable than array.reverse.

---

### Post by stchman on 2011-12-15
I know how to do it in Java, and from my understanding C# syntax is VERY close to Java's.

```

public static void arrayReverse( int[] data ) {
        int left  = 0; // index of leftmost element
        int right = data.length - 1; // index of rightmost element
  
        while (left < right) {
                // exchange the left and right elements
                int temp = data[ left ]; 
                data[ left ] = data[ right ]; 
                data[ right ] = temp;
     
                // move the bounds toward the center
                left++;
                right--;
        }
}

```

---

### Post by Tarast on 2012-01-12
No ur totaly right, ur way is actually better than array.reverse

---

### Post by KdotJ on 2012-01-12
> **Tarast said:**
> No ur totaly right, ur way is actually better than array.reverse

Out of interest, why is it?
I know that not all languages have such a built in method, but many of the main ones do. Plus, I'm sure the guys at Microsoft/Oracle have good algorithms in there ;)

---

