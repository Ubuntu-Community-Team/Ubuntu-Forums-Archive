---
title: "[SOLVED] Reading ISO-8859-1 in Java."
date: 2008-06-19
forum: Programming Talk
---

### Post by achelis on 2008-06-19
Hi.

I need to read an xml-file in Java that's encoded with ISO-8859-1. Parsing the file is not a problem, but special characters are not decoded correctly. I have checked with a hex editor and the input file is correctly encoded.

Here is a peace of the code I use to create my Reader:

```

FileInputStream fis = new FileInputStream(xmlFile);
InputStreamReader isr = new InputStreamReader(fis,Charset.forName("ISO-8859-1"));
XMLReader xmlReader = XMLReaderFactory.createXMLReader();
xmlReader.setContentHandler(handler);
xmlReader.setErrorHandler(handler);
xmlReader.parse(new InputSource(isr));

```

---

### Post by xlinuks on 2008-06-19
Hi,
looks like should work,
please post your file to be read and your source code for us to test it.

---

### Post by jespdj on 2008-06-19
The code looks fine. Are you sure the problem is in the decoding? What is your program doing with the decoded data? Maybe the problem is further on in your application.

---

### Post by achelis on 2008-06-19
Your suggestions made me write a much smaller app, with the purpose of testing this also it would be a bit much to post the entire app for you guys to look for bugs.

```

	public static void main(String[] args) throws IOException
	{
		File xmlFile = new File("20080618.txt");
		FileInputStream fis = new FileInputStream(xmlFile);
		InputStreamReader isr = new InputStreamReader(fis, Charset.forName("ISO-8859-1"));
		System.out.println(isr.getEncoding());
		try
		{
			while (isr.ready())
			{
				System.out.print("" + (char) isr.read());
			}
		} catch (IOException e)
		{
			throw e;
		} finally
		{

			isr.close();
		}
	}

```

The xml-file is attached.

---

### Post by xlinuks on 2008-06-19
Unfortunately I couldn't read the special characters with any editor (to make sure that the characters are not broken). How do you know that the characters have been written correctly to the file, in other words, do you have any text editor that displays the characters correctly?

PS: the ghex2 editor couldn't show the characters either.

---

### Post by achelis on 2008-06-19
Ah :)

You're right. The encoding was wrong. I checked the file first, but then after I checked it I edited it eclipse, which must have changed the encoding when I saved the file.

Thanks for your time. Problem solved :)

---

### Post by xlinuks on 2008-06-19
You're welcome :)

---

