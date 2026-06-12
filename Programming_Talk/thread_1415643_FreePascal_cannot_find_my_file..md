---
title: "FreePascal cannot find my file."
date: 2010-02-25
forum: Programming Talk
---

### Post by MuteClown on 2010-02-25
I saw the beginner programming challenge and thought i'd give it ago in using FreePascal, i am new to pascal and i am hitting a stumbling block which i can't get over. 
When ever i try and assign my file i get "Runtime Error 2" which means it can't find my file, i know i have the address right "/home/mute/mute.txt", i even tried it with it being in the same folder no luck. I have searched the internet for a solution but no luck yet, i have tried dozens of diffrent source code to see if it will work but all stops on

```

Assign(FileT, '/home/mute/mute.txt');

```

I have tried both AssignFile and Assign, to no avail. I really need some help on this:confused:

I determined to get it working so please help, i have read documents for few hours now and my brain is mush, i just hope someone can help.

---

### Post by gmargo on 2010-02-25
Do you need a Reset?  I got this to work; it opens and reads file Test.txt:
```

program pascaltest1;

var
    myFile : TextFile;
    text   : string;

begin
    Assign(myFile, 'Test.txt');
    Reset(myFile);

    while not Eof(myFile) do
    begin
        ReadLn(myFile, text);
        Writeln(text);
    end;

    Close(myFile);
end.

```

---

### Post by MuteClown on 2010-02-25
> **gmargo said:**
> Do you need a Reset?  I got this to work; it opens and reads file Test.txt:
```

program pascaltest1;

var
    myFile : TextFile;
    text   : string;

begin
    Assign(myFile, 'Test.txt');
    Reset(myFile);

    while not Eof(myFile) do
    begin
        ReadLn(myFile, text);
        Writeln(text);
    end;

    Close(myFile);
end.

```

Still wont work, i used the debugger and still stops at 

```

  Assign(myFile, 'Test.txt');

```


Edit:
Never mind solved it, it just when i executed it through Lazarus it wouldn't work but using terminal to execute it worked. Thank you for your response.

---

