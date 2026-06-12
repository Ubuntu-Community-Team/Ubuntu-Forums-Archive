---
title: "Need some help understanding instances in Python classes"
date: 2012-02-15
forum: Programming Talk
---

### Post by Kimm on 2012-02-15
Hello again everyone!

I've started learning Python and don't quite understand how Classes in Python work. For example, I have a class that handles writing to .CSV-files and I want to create several instances of it that handles different data-sets. This is my "Writer" code:

```

class CSV:
	csvFile = [];
	
	def Write(self, row, column, text):
		while len(self.csvFile) <= row:
			self.csvFile.append('');
			
		while len(self.csvFile[row].split(';')) <= column:
			self.csvFile[row] += ';';
			
		new = self.csvFile[row].split(';');
		
		new[column] = text;
		
		self.csvFile[row] = ';'.join(new);

	def Save(self, filename):
		text_file = open(filename, 'w');
		
		for s in self.csvFile:
			text_file.write(s+'\n');
			
		text_file.close();

```

I can only assume that I am using "self" incorrectly, but I'm having some issue finding a clear explanation of how to handle this. Now, I have created three instances of this class and am trying to write data to three different files, for example:

```

pop_writer = CSV();
age_writer = CSV();
gen_writer = CSV();

age_writer.Write(0,0,str(<average age>));
gen_writer.Write(0,0,str(<proportion of females>));
pop_writer.Write(0,0,str(<population size>));

age_writer.Save('test.csv');
gen_writer.Save('test2.csv');
pop_writer.Save('test3.csv');


```

Now, the problem is (as you can probably imagine), all three files are identical because it seems all of my declarations write to the same instance of the class.

I can only imagine that I am referencing the instance wrong inside the class! But I cant find any clear description of how this works.

Any help would be appreciated :)

---

### Post by Tony Flury on 2012-02-15
> **Kimm said:**
> Hello again everyone!

I've started learning Python and don't quite understand how Classes in Python work. For example, I have a class that handles writing to .CSV-files and I want to create several instances of it that handles different data-sets. This is my "Writer" code:

```

class CSV:
	csvFile = [];
	
..... rest of code snipped for brevity ....

```

Now, the problem is (as you can probably imagine), all three files are identical because it seems all of my declarations write to the same instance of the class.

I can only imagine that I am referencing the instance wrong inside the class! But I cant find any clear description of how this works.

Any help would be appreciated :)

Your declaration of 
```

csvFile = [];

```
Declares it as a class variable - and therefore all instances share the same data. Since you want this to be an instance variable, I would remove that line and include the following in your class definition : 
```

def __init__( self ):
    self.csvFile=[]

```

This creates csvFile as an instance variable/attrribute - and your code should work as intended.

```

class a:
	data = []
	def append( self, var ):
		self.data.append( var )
	def write(self):
		for i in self.data:
			print i

class b:
	def __init__(self):
		self.data = []
	def append( self, var ):
		self.data.append( var )
	def write(self):
		for i in self.data:
			print i

print "Class variable"
a1,a2 = a(), a()
a1.append("apples")
a2.append("pears")
a1.write()
a2.write()
print "Instance Variables"
b1, b2 = b(), b()
b1.append("bears")
b2.append("beer")
b1.write()
b2.write()

```
Code snippet demonstrates the differences.

---

### Post by Kimm on 2012-02-15
Thank you very much! This did indeed solve it :D

---

