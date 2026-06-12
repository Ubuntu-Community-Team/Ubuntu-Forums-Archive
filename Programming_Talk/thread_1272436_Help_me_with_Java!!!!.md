---
title: "Help me with Java!!!!"
date: 2009-09-22
forum: Programming Talk
---

### Post by humphreybc on 2009-09-22
Hi there,

I'm having difficulty completing this java assignment we've got... basically I'm trying to make a program that reads some numbers from a file using Scanner, and then use the numbers to form an ArrayList, then from that ArrayList these numbers are used to create new Rectangle objects with varying colour, fill, size and position on the screen.

These are the problems i'm having:

1) Trying to get the while loop in FilePanel.java to read 6 int values at each repetition.

2) The first integer from each line, representing fill/draw, needs to be turned into a boolean true/false. (If-else statement).

3) The second colour variable needs to be turned into a Color. So I have to set a variable to Color.red for a 0, Color.blue for 1, Color.green for a 2 etc...

At the moment I have the program printing the numbers just to test whether it's reading from the file correctly. I'm getting a "NoSuchElementException" error each time I run the program though and i'm not sure what for as it compiles correctly.

Any help would be appreciated, files are attached :)

Thanks!

---

### Post by Ruhe on 2009-09-22
Hi.

Never do things like fileScan.nextInt() without checking that nextInt() exists.
This is your mistake, you are trying to get next integer from scanner, but it doesn't exist. I'll show you a little modified code, I hope you'll find the right direction to proceed.


This is rewritten while loop, it iterates each line, then parses numbers in the line. Don't forget to fix the order, to collect right coordinates x and y, and dimensions.
```

while (fileScan.hasNextLine()) {
        boolean fill = fileScan.nextInt()==1? true : false; // 1=>true, 0=>false
        Color color = getColor(fileScan.nextInt());

        // FIXME: fix the order of statements
        int x = fileScan.nextInt();
        int y = fileScan.nextInt();
        int width = fileScan.nextInt();
        int height = fileScan.nextInt();

        Rectangle r = new Rectangle(fill, color, x, y, width, height);
} 

```

And this is a method which returns specific Color:
```

// if nothing found returns black color
private static Color getColor(int color) {
    Color c = Color.BLACK;
    switch(color) {
        case 0: c = Color.RED;
        case 1: c = Color.BLUE;
        case 2: c = Color.GREEN;
        case 3: c = Color.YELLOW;
    }
    return c;
}

```

---

### Post by humphreybc on 2009-09-22
Thankyou!! I'll give it a shot today with your suggested changes and see how I go :)

---

