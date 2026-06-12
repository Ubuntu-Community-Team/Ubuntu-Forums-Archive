---
title: "Java show and hide words"
date: 2011-11-20
forum: Programming Talk
---

### Post by tuket on 2011-11-20
Hello, I have done a program  in java which is the game of scissor paper and rock.
I consists in the following:
Player 1 indroduces scissor, paper or rock, then player 2 do the same. Scissor wins to paper, paper wins to rock and rock wins to scissor.
But I have a problem.
```
tuket@tuket-desktop:~/5$ java ppt
Say : rock, paper or scissor
Player 1:
scissor


Player 2:
paper
Player 1 wins
tuket@tuket-desktop:~/5$ 

```
When player 1 introduces the word then player two can see it. So I want it to disapear when enter is pressed.
I hope you understand it, I know my english is not very good. ;)

---

### Post by ju2wheels on 2011-11-20
Try java.io.Console's readPassword function so that you read a line with echoing disabled:

[http://download.oracle.com/javase/6/docs/api/java/io/Console.html]("http://download.oracle.com/javase/6/docs/api/java/io/Console.html")

---

### Post by tuket on 2011-11-21
Thank you it is useful but it is not exactly what I wanted.What I want is to echo and then erase but if I dont find any way I'll use the method readPasswod(). Can any one help please:confused:

---

### Post by ju2wheels on 2011-11-21
You would need to have control of the console to do that, the only other way I can think of is to use something like ncurses:


[http://sourceforge.net/projects/javacurses/]("http://sourceforge.net/projects/javacurses/")

---

### Post by jamescox84 on 2011-11-21
You could use some terminal control characters.  So once the user has entered their choice you move the cursor backup to the line where the prompt was, then to the left until you get to the point where the user started typing.  Then just print spaces, or as I have in this example, stars over the input.

```

package rsp;

import java.io.*;


public class Rsp {
    public static void main(String[] args) throws Exception {
        String prompt = "Enter command: ";
        
        // Setup a reader for stdin.
        BufferedReader stdin = new BufferedReader(new InputStreamReader(System.in));
       
        // Prompt the user for a command.
        System.out.print(prompt);
        System.out.flush();
        
        // Read the users command.
        String command = stdin.readLine();
        
        // Move cursor back up to the previous line.
        System.out.print("\u001b[A");
        // Move cursor to the end of the prompt, char-at-a-time.
        for (int i = 0; i < prompt.length(); ++i) {
            System.out.print("\u001b[C");
        }
        // Blank the chars enter by the user.  I'm using '*' but you could use ' '.
        for (int i = 0; i < command.length(); ++i) {
            System.out.print('*');
        }
        // Move back to the next line.
        System.out.println();
        // Make sure commands are sent to the terminal with a buffer flush.
        System.out.flush();
    }
}

```

Just one small note with this solution, it requires a compatible terminal.  Any terminal on Linux/UNIX will work.  The terminal in NetBeans (if you are using it) is not compatible and will print some strange output if the program runs in it.

Output looks like this in a compatible terminal:
```

Enter command: this is my command.

```

when the user hits enter it is changed to:

```

Enter command: *******************

```

---

### Post by tuket on 2011-11-22
Thank you for the answres im going to try and i'll tell you :)

---

