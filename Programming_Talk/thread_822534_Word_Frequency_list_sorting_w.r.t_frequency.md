---
title: "Word Frequency list sorting w.r.t frequency"
date: 2008-06-08
forum: Programming Talk
---

### Post by true_friend on 2008-06-08
&#65279;HI

I am a c# learner I've created a small application which reads text from a text file, splits it to array then this array is passed to a sortedlist in this way that if the word is already in sortelist it adds 1 to value (which is int and key which is string). else it will be added with like (key, 1). Sortedlist sorts the keys automatically (In alphabetical order). I want to sort it w.r.t frequency which in this case is values. How can I do this? I am pasting the code I've written for alphabetical freq list.

```
using System;

using System.IO;

using System.Text;

using System.Collections;

using System.Collections.Generic;

namespace Occurance

{

	class Occurance

	{

		static void Main()

		{

			StreamWriter sw1 = new StreamWriter(@"F:\filefreq.txt");

			

			char[] delim = new char[] { 

                ' ', ',', ';', ':', '.', '!', '?', '/', '\\', '\r', '\n', '\'', '"', '–', '-', '_', 

                '~', '&', '+', '*', '\x00b1', '%', '@', '#', '(', ')', '{', '}', '[', ']', '“', '”', 

                '$'

             };

			StreamReader sr = new StreamReader(@"F:\Art-001.txt");

			SortedList<string, int> slist = new SortedList<string, int>();

			string[] sarray = sr.ReadToEnd().ToString().ToLower().Split(delim, StringSplitOptions.RemoveEmptyEntries);

			foreach(string s in sarray)

			{

				if(slist.ContainsKey(s) == true)

				{

					slist[s] = slist[s]+1;

				}

				else

				{

					slist.Add(s, 1);

				}

			}

			foreach(KeyValuePair<string, int> kvp in slist)

			{

				sw1.WriteLine("{0, -20}		{1}", kvp.Key, kvp.Value, true);

			}

			sw1.Close();
		}

	}

}




```

Regards

---

### Post by mike_g on 2008-06-08
You could check out the api to see if theres any methods for sorting by value. If not you could write your own sort algo. A 'selection sort' or 'bubble sort' would be easy to learn. (Although they are pretty slow)

---

