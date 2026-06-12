---
title: "[java]String Object Problem"
date: 2008-10-04
forum: Programming Talk
---

### Post by Pyro.699 on 2008-10-04
Hello,

I used the code:

```

File f = new File(file);
        FileReader fr = new FileReader(f);
        LineNumberReader lnreader = new LineNumberReader(fr);
        
        String line = "";
        
        while ((line = lnreader.readLine()) != null){
            String[] spl = line.split("(?<!\\\\)\\.");

```

to read each line of a file and then split it accordingly. I end up with a String[] with 4 sections. spl[0] to spl[3], what i need to do is check to see if spl[0] is equal to another string like:

```

if(spl[0] == "This")

```

Ive tried several things like:

```

if(spl[0] == "This"){}
if(spl[0].equalsIgnoreCase("This")){}
if(spl[0].toLowerCase("This")){}

```

I have a feeling that spl[0] is not a string object or anything.

Thanks
~Cody Woolaver

---

### Post by mike_g on 2008-10-04
Maybe something like:
```
if (spl[0].toLowerCase().equals("this"))
```
You cant use the equality operator in strings in Java. instead use the string .equals() method.

Cheers.

---

### Post by Pyro.699 on 2008-10-04
Ill try to go into more depth with my program because it didnt work...

This is the file that is being read
```

Process.List..a7fad20aa0662e9ee31e39ea7367e4b1
Process.Kill{pid}.523543.8a766fdadc85232b26fbcacfc4256137
Process.Kill{name}.gedit.aa8f8f8c89bb8f7d1695694a96dc9a75

```

This section reads the lines and splits them bassed on "." as long as its not "\."
```

        File f = new File(file);
        FileReader fr = new FileReader(f);
        LineNumberReader lnreader = new LineNumberReader(fr);
        
        String line = "";
        
        while ((line = lnreader.readLine()) != null){
            String[] spl = line.split("(?<!\\\\)\\.");            
            //Main ======= spl[0]
            //Secondary == spl[1]
            //Command ==== spl[2]
            //Hash ======= spl[3]

```
This is the section of code that process' the lines
```

//The Process Command
                else if(spl[0].equalsIgnoreCase("Process")){
                    //List
                    if(spl[1].equalsIgnoreCase("List")){
                        Process p1 = Runtime.getRuntime().exec("ps -u cody");
                        InputStreamReader reader = new InputStreamReader ( p1.getInputStream () );
                        BufferedReader buf_reader = new BufferedReader ( reader );
                        String lne,total="";
                        
                        while ((lne = buf_reader.readLine ()) != null)
                        {
                            total += lne+"\n";
                        }
                        
                        System.out.println("Process:List");
                        addToUpFile("["+spl[3]+"]\n"+total);
                    }
                    //Kill{pid}
                    else if(spl[1].equalsIgnoreCase("Kill{pid}"))    
                    {
                        //TODO make sure the process existed to begin with
                        Process p2 = Runtime.getRuntime().exec("kill "+spl[0]);
                        p2.waitFor();
                        //TODO make sure that the process is gone now that the application has been run
                        //TODO send return data base on previous results
                        System.out.println("Process:Kill{pid}");
                        addToUpFile("["+spl[3]+"]\n"+"Done!");
                    }
                    //Kill{name}
                    else if(spl[1].equalsIgnoreCase("Kill{name}")){
                        //TODO ... All of this section -.- im too lazzy to do it right now
                        //TODO basically use 'ps -u cody' to get the process' and then search eachline and get the pid, kill that
                        //TODO send return value
                        System.out.println("Process:Kill{name}");
                        addToUpFile("["+spl[3]+"]\n"+"Done!");
                    }
                }

```

---

### Post by pp. on 2008-10-04
> **Pyro.699 said:**
> I have a feeling that spl[0] is not a string object or anything.

What kind of thing is spl[0], then?

---

### Post by Pyro.699 on 2008-10-04
It is suppose to be a string object, but its not acting as one.

---

### Post by pp. on 2008-10-04
> **Pyro.699 said:**
> It is suppose to be a string object, but its not acting as one.

Java - like most other languages - can determine the type of any given object. There's no need to suppose anything about an object in the program. With a modest amount of coding, you can determine the type and the value of any object.

---

### Post by Pyro.699 on 2008-10-04
Then can you explain why the code above doesn't seem to work?

---

### Post by pp. on 2008-10-04
Sorry, I have neither the time, the capability nor the inclination to analyse your code for you.

I gave you the very broad hint that you have all tools at your disposal to determine the cause of the problem you wish to solve. The hint consisted of adding a few lines of debugging code to your program which tells you the class and the value of the item you suppose to be a string.

---

