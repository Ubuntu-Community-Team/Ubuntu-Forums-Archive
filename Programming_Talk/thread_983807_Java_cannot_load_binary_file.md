---
title: "Java cannot load binary file?"
date: 2008-11-16
forum: Programming Talk
---

### Post by exhume on 2008-11-16
I am in the process of teaching myself java. In order to do this I gave myself a rather large and complicated multi-part project to complete. The first portion of this project involved creating a small program that takes data and turns it into binary files. This program works no problem. The next step is a program that reads in all of these files and then uses them for various things. I created a number of these binary files (around 50) and was able to open them using the first program, but in the new program i am writing, these binary files fail to open using the same method from the same class that I used in the original program. I am posting the pertinent code here:

```
public void load()
	{
		File ruledirectory = new File("../../../rules");
		File [] rulebins = ruledirectory.listFiles();
		int listsize = rulebins.length;
		list = new rule[listsize];
		String filename;
		for(int i = 0; i < listsize; i++)
		{
			filename = rulebins[i].getName();
			if(filename.endsWith(".bin"))
			{
				System.out.println("Binary File " + filename +" Loading!"); 
				this.list[rulecount] = new rule("Placeholder", false, "Placeholder", "Placeholder", 1);
				this.list[rulecount].open(filename);
				this.rulecount++;
			}
		}
	}
```

I will also post both the save and open methods from the rule class:

```
public void save(String file)
	{
		try
		{
			ObjectOutputStream filew = new ObjectOutputStream(new FileOutputStream(file));
			filew.writeUTF(this.name);
			filew.writeBoolean(this.optional);
			filew.writeUTF(this.summary);
			filew.writeUTF(this.book);
			filew.writeInt(this.page);
			filew.close();
		}
		catch(IOException e)
		{
			System.out.println("Error Saving File");
		}
		
	}
```

```
public void open(String file)
	{
		try
		{
			ObjectInputStream filer = new ObjectInputStream(new FileInputStream(file));
			this.name = filer.readUTF();
			this.optional = filer.readBoolean();
			this.summary = filer.readUTF();
			this.book = filer.readUTF();
			this.page = filer.readInt();
			filer.close();
		}
		catch(IOException e)
		{
			System.out.println("Error Reading File");
		}
	}
```

Any ideas as to what is causing my problem? The exception is being thrown for the oepning of every single file. But I can open all of them with the original program. Thans for the help in advance!

---

### Post by achelis on 2008-11-16
Maybe I missed it in your post, but what exception did you get? (replace your Sysout with e.printStackTrace() to see it.

My guess is that the problem is related to serialization. ObjectIn/OutputStream uses serialization to read/write your data. I've never used it myself, but as far as I recall it causes problem if the classes you've stored changes.

If I understand you right, the original program without any changes to the stored objects opens with no problems - which makes sense as this is how it should work, but the new program can't open them because the stored objects no longer matches the class... (this is a guess - seeing the exception might make more sense of what is happening.)

Anyway - rather than listening to my babbling I'd suggest you read up on Object-serialization.

[http://java.sun.com/j2se/1.5.0/docs/api/]("http://java.sun.com/j2se/1.5.0/docs/api/") : Look for ObjectInputStream and ObjectOutputStream.

I'll do a quick Google and see if I can find more links for you..

You might also want to try the more raw data way of storing stuff - depends on your needs really.

---

