---
title: "Creating and checking File object (Java)"
date: 2012-07-04
forum: Programming Talk
---

### Post by Drenriza on 2012-07-04
Hey guys.

I'am trying to create a object of **File**.

And well i think it's going ok ,) The purpose is to create two objects of two different paths, put these into an ArrayList and then run through the ArrayList checking if the paths exist.

But i cant really seem to get it to work.

```
public void checkFolders()
    {
        FileConstructor FC = FileConstructor.getInstance();
        FileConstructor fc = null;
        File file = null;
        
        ArrayList folders = new ArrayList();
        folders.add(fc = new FileConstructor(file = new File("/root/2m-of")));
        folders.add(fc = new FileConstructor(file = new File("/root/2m-of/outputFolder")));
    }
```

The constructor is as follows
```
public class FileConstructor 
{
    private static FileConstructor lInstance;
    
    public static FileConstructor getInstance()
    {
        if (lInstance == null)
        {
                lInstance = new FileConstructor();
        }

        return lInstance;
    }
    
    FileConstructor()
    {}
    
    private File path;
    
    FileConstructor(File path)
    {
        this.path = path;
    }
    
    public File getPath()
    {
        return path;
    }
}
```

```
public void checkFolders()
    {
        FileConstructor FC = FileConstructor.getInstance();
        FileConstructor fc = null;
        File file = null;
        
        ArrayList folders = new ArrayList();
        folders.add(fc = new FileConstructor(file = new File("/root/2m-of")));
        folders.add(fc = new FileConstructor(file = new File("/root/2m-of/outputFolder")));

[B]//The problem is here where i CANT say
for(Object object : folders)
{
  if(object. << i cannot say _exist()_ here. So how can i access this function?
  {do something}[/B]
}
    }
```

Am i on the right track or am i just WAYYYYYY out their?

---

### Post by PaulM1985 on 2012-07-04
I think you only need to be using the File class for this.

You would have something like:
```

File directory = new File("/a/directory");
if (!directory.exists())
{
   // Doesn't exist, so make it
   directory.mkdir();
}
else 
{
   // It already exists
   if (!directory.isDirectory())
   {
      // Oh no, someone has added a file where this directory should be
   }
}

```

Paul

---

### Post by r-senior on 2012-07-04
You could cast your Object but you'd be better off using generics:

```

List<File> files = new ArrayList<File>();

files.add(new File("/root/2m-of"));
files.add(new File("/root/2m-of/outputFolder"));

for (File file : files) {
    if (file.exists()) {
        // Do something with file
    }
}

```

I'm not quite sure where you are going with the FileConstructor (which is a a bit like a factory as far as I can see). Was the idea to set a base path on the factory and use it to create File objects relative to that path perhaps?

---

### Post by Drenriza on 2012-07-04
Hey Paul.

Yes but my problem was that i have multiple paths that i need to check, how would you check that without some sort of list and run through it?

r-senior
Uhmm had to read up on what a factory is :)

The idea i had when i created the code.

#1 Create a file object of the path to check.
#2 Add the created object to the arraylist.
#3 Run through the arraylist, checking each object for if it exist.

But i'm not sure if i'am even close to reaching that goal. After fiddling with it for a while.

---

### Post by PaulM1985 on 2012-07-04
> **Drenriza said:**
> Hey Paul.

Yes but my problem was that i have multiple paths that i need to check, how would you check that without some sort of list and run through it?


Just wrap the code I gave you in a for loop...

```

ArrayList<String> directoryPaths = new ArrayList<String>();
directoryPaths.Add("/a/path");
for (String s : directoryPaths)
{
File directory = new File(s);
if (!directory.exists())
{
   // Doesn't exist, so make it
   directory.mkdir();
}
else 
{
   // It already exists
   if (!directory.isDirectory())
   {
      // Oh no, someone has added a file where this directory should be
   }
}
}

```

---

### Post by Drenriza on 2012-07-05
Thanks for the help and your time guys.

---

