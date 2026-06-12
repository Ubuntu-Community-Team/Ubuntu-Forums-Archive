---
title: "Problem detecting EOT, CR and LF in Java."
date: 2011-03-08
forum: Programming Talk
---

### Post by Gunnlaugur on 2011-03-08
Hello

I have a program I use to receive stream containing alarms from telephone exchanges.
My program is started with inetd when the exchange hooks up and is alive as long as there is a stream comming through. 

In the stream there is a hex value "040D0A" indicating EOT, CR and LF.
My problem is I'm not able to detect it :confused:

Here is a portion of my code.

```

while ((line = br.readLine()) != null) {
    ...
    some code block to parse input
    ...
    if (line.contains("\r\n") || line.contains("END")) {
       ...
       some code to commit data to database
       ...
    }
}

```What am I doing wrong trying to detect EOT, CR and LF?

Any advice would be greatly appreciated.

---

### Post by Arndt on 2011-03-08
> **Gunnlaugur said:**
> Hello

I have a program I use to receive stream containing alarms from telephone exchanges.
My program is started with inetd when the exchange hooks up and is alive as long as there is a stream comming through. 

In the stream there is a hex value "040D0A" indicating EOT, CR and LF.
My problem is I'm not able to detect it :confused:

Here is a portion of my code.

```

while ((line = br.readLine()) != null) {
    ...
    some code block to parse input
    ...
    if (line.contains("\r\n") || line.contains("END")) {
       ...
       some code to commit data to database
       ...
    }
}

```What am I doing wrong trying to detect EOT, CR and LF?

Any advice would be greatly appreciated.

The description of readLine says this:

"Returns:
    A String containing the contents of the line, not including any line-termination characters, or null if the end of the stream has been reached"

So \r and \n will never be there.

---

### Post by Gunnlaugur on 2011-03-08
Thanks Arndt
What would then be the correct way to detect it?
-Gunnlaugur

---

### Post by Arndt on 2011-03-08
> **Gunnlaugur said:**
> Thanks Arndt
What would then be the correct way to detect it?
-Gunnlaugur

You want to know if the character with ASCII value 4 is the last character in the string, or perhaps that it is the only character in the string. I don't know Java, but the suitable string functions should exist.

---

### Post by PaulM1985 on 2011-03-08
It looks like you are using a Scanner.  Have you tried using an InputStreamReader?  You would then be able to use:

```

StringBuffer stringBuf = new StringBuffer();
while ((myInt = reader.next()) != -1)
{
   if (myInt == SOME_DELIMITER)
   {
      // special code relating to the delimiters you want to
      // pick up on
   }
   else
   {
      // Here is where we are building up the line
      // which is the equivalent to the "line" variable in
      // your code.
      stringBuf.append((char) myInt);
   }
}

```

Paul

---

