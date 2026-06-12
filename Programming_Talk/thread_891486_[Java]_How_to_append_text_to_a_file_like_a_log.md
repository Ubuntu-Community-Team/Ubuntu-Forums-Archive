---
title: "[Java] How to append text to a file like a log?"
date: 2008-08-16
forum: Programming Talk
---

### Post by Zdravko on 2008-08-16
Hi!
I am about to write a small Java application, that will eventually run on a Windows machine. The program will generate a lot of output and it will be printed on the console via the System.out.* functions. But the program will run for a long time and I want to make things better, by printing in a text file too. 
What should I use for appending text to a file? I prefer a simple, but fast method. Since the user might want to cancel the program, I want all output to be already written to the file so that the file is not lost, when not properly closed.
Any ideas?
Thanks in advance!

P.S. I tried to ask this in a java IRC channel, but the guys there seemed to be even ignorant as me.

---

### Post by NovaAesa on 2008-08-16
```

PrintWriter outFile = new PrintWriter("fileName.txt"); //opens file
outFile.println("what you want to write"); //writes to file
outfile.close(); //closes the file

```

Nothing too bad happens if you don't close the file. Also, unless you are staring off with a fresh file, you might want to find a way of reading all the entries, storing in an array and then printing them back. Either that or find a way that will actually append.

---

### Post by myrtle1908 on 2008-08-16
[PHP]String filename= "MyDataFile.txt";
boolean append = true;
FileWriter fw = new FileWriter(filename,append);
fw.write("add a line\n");//appends the string to the file
fw.close();[/PHP]

---

### Post by Zdravko on 2008-08-16
Thanks to both of you. But in the mean time I tried this:
[PHP]
try {
            bw = new BufferedWriter(new FileWriter("results.txt", true));
} catch(Exception e) {
            System.out.println(e); 
            e.printStackTrace();
}
...
    try {
for (;;) {
        bw.write("some text...");
        bw.newLine();
        bw.flush();
}
} catch(Exception e) {
            System.out.println(e); 
            e.printStackTrace();
}
[/PHP]
I noticed, that canceling the program with Ctrl+C is not a problem, because the file is flushed after each write operation.
I think that I managed it! What do you think?

---

### Post by NovaAesa on 2008-08-16
That certainly works as well. That's one of the great things about Java, there are many ways to do the same thing.

---

