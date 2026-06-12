---
title: "Simple Java question"
date: 2011-07-04
forum: Programming Talk
---

### Post by abraxas334 on 2011-07-04
I am trying to use a simple Config file rather than command line arguments in order to read in some data.

Say normally I want to set some parameters from commndline like this:
[PHP]
kT_i = StringTools.toDouble(arguments[0]);
            kT_step = StringTools.toDouble(arguments[1]);
            nsolvent = StringTools.toInt(arguments[2]); 
            nTemps = StringTools.toInt(arguments[3]);

[/PHP]

now rather than doing that I would like to read them from a file, where the file content may be something like this:
1 1 1 1. I can get as far as reading the line in the file to a string. See below, but how can i then assign my individual values to my variables?

[PHP]try{
                
                String filename = "Configfiles/Config."+TaskID+".dat";
                FileInputStream fstream = new FileInputStream(filename);
                  // Get the object of DataInputStream
                  DataInputStream in = new DataInputStream(fstream);
                  BufferedReader br = new BufferedReader(new InputStreamReader(in));
                  String strLine;
                  //Read File Line By Line
                  while ((strLine = br.readLine()) != null)   {
                  // Print the content on the console
                  System.out.println (strLine);
                  }
                   in.close();             
                
            }catch(Exception e){
                System.err.println("Error: "+e.getMessage());
                
            }[/PHP]

Any help is appreacitated thanks :)

---

### Post by Petrolea on 2011-07-04
Split it and save pieces into array, then you can assign pieces of array to variables.

---

### Post by ve4cib on 2011-07-04
> **Petrolea said:**
> Split it and save pieces into array, then you can assign pieces of array to variables.

Agreed.  <String>.split("\\s+") is your friend in this instance.

---

### Post by Some Penguin on 2011-07-04
> **abraxas334 said:**
> I am trying to use a simple Config file rather than command line arguments in order to read in some data.

Consider using java.util.Properties, or more flexible if slightly more complicated, org.skife.config-magic.  This a frequently-reinvented wheel.  config-magic is quite flexible.  Both can retrieve from system properties, making it simpler to override parameters via -Dfoo=bar.

[http://download.oracle.com/javase/6/docs/api/java/util/Properties.html](http://download.oracle.com/javase/6/docs/api/java/util/Properties.html)
[https://github.com/brianm/config-magi](https://github.com/brianm/config-magi)

> 

```
try{
                
                String filename = "Configfiles/Config."+TaskID+".dat";
                FileInputStream fstream = new FileInputStream(filename);

```


Bad.  Declare the FIS outside the 'try' block, so you can reference it in a 'finally' block which ensures closure.  Otherwise, you're relying on finalizers or the like to save you when things go wrong.  You're asking for a file handle leak.

> 
```

                  // Get the object of DataInputStream
                  DataInputStream in = new DataInputStream(fstream);
                  BufferedReader br = new BufferedReader(new InputStreamReader(in));

```

And what if you're running this on e.g. a Mac, where the system character set is likely a MacRoman variant, while the input was written using UTF-8?  The two-argument constructor is preferred for ISR.  And you don't need to pass in a DataInputStream if you're going to create a BufferedReader -- you can just use the FileInputStream.

> 
```

                  String strLine;
                  //Read File Line By Line
                  while ((strLine = br.readLine()) != null)   {
                  // Print the content on the console
                  System.out.println (strLine);

```


If you feel like reinventing the wheel, the next obvious step is to parse the line.  Regular expressions work, but are possibly overkill -- if you define it as "foo=bar", where foo must not have any equals signs (quoted or otherwise) and 'bar' must not have newlines, it's trivial to parse.  If you allow comments e.g. EOL comments from #, then you want to provide an escape mechanism so such can be used in 'bar'.

> 
```

                  }
                   in.close();             
                
            }catch(Exception e){

```


Bad exception handling.  'catch (Exception e)' is almost never a good idea.

> 
```

                System.err.println("Error: "+e.getMessage());
      

```    


Not a fan of having stack traces to help you track down why an exception happened, eh?

> 
```
      
            }

```


Any help is appreacitated thanks :)[/QUOTE]

---

