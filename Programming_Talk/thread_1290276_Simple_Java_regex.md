---
title: "Simple Java regex"
date: 2009-10-13
forum: Programming Talk
---

### Post by cdiem on 2009-10-13
EDIT: Solved it, using the classes Pattern and Matcher and ""<uppercase>(.*?)</uppercase>" as regex. Thread can be closed/deleted. 


Hello, 

I'm trying to search+replace in a java String, but I feel my regular expression is not right:

[PHP]public static void main(String[] args) {
		String input = new String(
				"This is my test string. <uppercase>And some</uppercase> more text. "
						+ "And the end <uppercase>of it</uppercase> for this program.");
		String regex = "<uppercase>(\\\\w+)</uppercase>";
		String output = input.replaceAll(regex, "$0.toUpperCase()");
		System.out.println(output);
	}
[/PHP]


The parts in "<uppercase>...</uppercase>" should be transformed in capital letters. I have spend quite some time searching in the internet, but I cannot seem to find out my mistake. Any help will be appreciated.

---

