---
title: "Java Scope problem"
date: 2011-02-28
forum: Programming Talk
---

### Post by Zalib on 2011-02-28
Alright I seem to be having a scope problem with my code. I'm just writing a simple program that inputs a number and gives the reverse. Problem is It doesn't give me what I want the output is zero which is obviously wrong. Here's the code:

```
import javax.swing.*;


public class Reverse_Program
{
    public static void main(String[] args)
    {
        String string_input;
        int num_input;
        
        string_input = JOptionPane.showInputDialog("Please input a number and I'll reverse it for you!");
        num_input = Integer.parseInt(string_input);
            
       
    }
    
    public static int reverse(int x)
    {
        int Num_Reversed = 0;
        
        while(x != 0)
        {
            
            Num_Reversed = Num_Reversed * 10;
            
            Num_Reversed = Num_Reversed * ( x % 10);
            
            x = x /10;
            
            
        }
       
         JOptionPane.showMessageDialog(null, "Your number reversed is: " + x, "BAM!", JOptionPane.PLAIN_MESSAGE);
        
    }
}
```The method I think is where the problem is but I just can't put my thumb on it. Any suggestions?

---

### Post by ve4cib on 2011-02-28
Your problem is with one of these two lines:

Num_Reversed = Num_Reversed * 10;
Num_Reversed = Num_Reversed * ( x % 10);


Num_Reversed is initialized to zero, and you only ever multiply with it.  That's why it's always giving you zero.

So what you need to do is to replace one of your multiplications with an addition.  I'll let you figure out which one.

---

### Post by schauerlich on 2011-02-28
Well, you never actually call the reverse method, or return the reversed number from that method...

---

### Post by Zalib on 2011-02-28
> Your problem is with one of these two lines:

Num_Reversed = Num_Reversed * 10;
Num_Reversed = Num_Reversed * ( x % 10);


Num_Reversed is initialized to zero, and you only ever multiply with it.  That's why it's always giving you zero.

So what you need to do is to replace one of your multiplications with an addition.  I'll let you figure out which one.You sir are awesome for picking that out and thank you for not telling me directly. Thanks! :D

> Well, you never actually call the reverse method, or return the reversed number from that method...

Yeah I actually forgot I put up old code. Good thing the problem was still solvable through this. :D Thanks for pointing that out.

---

