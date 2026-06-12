---
title: "terminal-command -&gt; c/c++ code?"
date: 2012-06-09
forum: Programming Talk
---

### Post by jaguzu on 2012-06-09
Hey!
I have a device that i read data from (in terminal) with "cat /dev/lirc0 | hexdump". 

[I]**0000000 **ffff    00ff  0a5a 0100 0352 0000 01c2 0100
**0000010**[/I] [I] 01c2 0000 01c2  0100 01c2 0000 01c2 0100
**0000020 **[/I] *0384 0000 0190 0100 0384 0000 0546 0100*

The thing i have tried to do is to get this data with c or c++ code in my Qt-application.
The best thing would be if i could get rid of the adress(the bold numbers) and get something like this:

[I]ffff   00ff  0a5a 0100 0352 0000 01c2 0100
[/I][I]01c2 0000 01c2  0100 01c2 0000 01c2 0100
[/I]*0384 0000 0190 0100 0384 0000 0546 0100*

My idea was to open the file and then read from it in the c/c++ code but it doesnt work. It seems to stop when im trying to read the data. 

attempt1 (with Qt):
[I]QFile file("/dev/lirc0");     //( "/dev/input/mice" to test mouse )
    if(file.open(QIODevice::ReadOnly)) 
        cout<<"wrong";
    else{
        QTextStream in(&file);
        cout << in.readAll(); }[/I]

attempt2 ("clean" c++)
[I]    ifstream f;
    f.open("/dev/lirc0");
    char out[100];
    if (f.is_open()) {
        while ( f.good() ) {
          f >> out;
          cout << out;
        }
        f.close();
    }[/I]

Anyone with a good solution? thanks :)

---

### Post by Tony Flury on 2012-06-09
in your second example try : 
```

ifstream f;
f.open("/dev/lirc0", ifstream::binary);

```

The default for opening a file will be in ASCII mode,

---

