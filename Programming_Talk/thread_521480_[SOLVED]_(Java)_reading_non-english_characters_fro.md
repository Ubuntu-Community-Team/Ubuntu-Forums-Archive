---
title: "[SOLVED] (Java) reading non-english characters from text file"
date: 2007-08-09
forum: Programming Talk
---

### Post by Balazs_noob on 2007-08-09
Hi guys

i am just started to learn Spanish and i have decided, that because
i am learning Java too i will write a software that will help me remember the words :)

it would just write the word in English and i would have to write the word in Spanish and it would check if it is good or not...

but i have a problem with reading in non-English characters
like á from the text file, it shows  some other weird symbol :(

Hope somebody can help a poor  student :)
Here is the code:
```

import java.io.*;

public class Input {
	
	public static void main(String[] args) throws IOException {	
			BufferedReader inputStream = null ;
			
			try {
				inputStream = new BufferedReader (new FileReader("spanish.txt"));

				String str ;				
				while ((str = inputStream.readLine())!=null){
					System.out.println(str);
				}
			} catch(FileNotFoundException e) {
				System.out.println("Bad file name!!");			
			} finally {
	            if (inputStream != null) {
	                inputStream.close();
	            }
			}
	}
}

```

i think i would need to change the char set

---

### Post by kknd on 2007-08-09
Java uses UTF-8 by default. It should work out-of-the-box.

Are you sure the document is ok? If it's not in UTF-8, try to export as it.

---

### Post by Ragazzo on 2007-08-09
You get garbled text when the file uses a different encoding. Use **file spanish.txt** to see what encoding the file is using. If it reports that the text is ISO-8859, use **iconv -f latin1 -t utf8 spanish.txt -o output.txt** to convert it.

---

### Post by Balazs_noob on 2007-08-10
Thanks guys you were right :)
i just had to changed the encoding of "spanish.txt"
in Gedit to utf-8 

Thanks again :popcorn:

---

