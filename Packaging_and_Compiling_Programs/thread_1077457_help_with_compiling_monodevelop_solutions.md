---
title: "help with compiling monodevelop solutions"
date: 2009-02-22
forum: Packaging and Compiling Programs
---

### Post by zizzdude on 2009-02-22
Hello, I'm trying to build a library as one project part of the solution, then a test project using that library. However, I get some strange errors.

library (in java):
```

package vocab;

import java.util.ArrayList;
import cli.System.String;
import cli.System.Console;

public class VocabWord
{
	private String myWord;
	private String[] myDefinitions;
	
	public VocabWord(String word)
	{
		myWord = word;
		myDefinitions = new String[0];
		Console.WriteLine("VocabWord made");
	}
	
	public void addDefinition(String definition)
	{
		// create a list one larger than current
		String[] temp = new String[myDefinitions.length + 1];
		
		// move all items from current to 
		for (int i = 0; i < myDefinitions.length; i++)
		{
			temp[i] = myDefinitions[i];
		}
		
		// add the "definition" to the list
		temp[myDefinitions.length - 1] = definition;
		
		myDefinitions = temp;
	}
	
	public String ReadDefinition(int index)
	{
		if (index > (myDefinitions.length - 1))
			return myDefinitions[myDefinitions.length - 1];
		return myDefinitions[index];
	}
	
	public String ToString()
	{
		return myWord;
	}

	public static void thing2(String arg)
	{
		cli.System.Console.WriteLine("thing2 method writes " + arg + "!");
	}		
}
		


```

test (in boo):
```

import System

word as VocabWord = VocabWord("thing")

word.addDefinition("its a thing")
VocabWord.thing2("what")

```

yet, I get the error:
```

Line 8: BCE0019: 'thing2' is not a member of 'VocabWord'.

```

Did I type anything wrong? or added the wrong assembly path? I added the vocab (library) project to the test project reference in monodevelop.

---

