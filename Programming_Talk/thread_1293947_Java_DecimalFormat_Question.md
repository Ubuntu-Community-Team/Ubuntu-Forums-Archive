---
title: "Java DecimalFormat Question"
date: 2009-10-17
forum: Programming Talk
---

### Post by s3a on 2009-10-17
Here is my code:

```
//import javax.swing.JOptionPane;
import java.text.DecimalFormat;

import java.util.Scanner;

public class decform_checker
{
	public static void main (String [] args)
	{
		Scanner kb = new Scanner(System.in);
		
[B]		double number = kb.nextDouble;
		//double number = 268.324825;[/B]
		
		DecimalFormat formatter = new DecimalFormat("#0000.000");
		System.out.println(formatter.format(number));
	}
}
```

If I were to uncomment that line that is bold, and comment the other line that is bold, my program would work but at the moment it does not! Could someone please tell me what I am doing wrong? (the compilation error says that it doesn't see a symbol on the line I have bold that is not commented)

Thanks in advance!

---

### Post by Reiger on 2009-10-17
'tis a simple matter of **spelling**. Or reading what you type, really.

It may be myself who has a bit too much experience as an idiot pounding a problem for hours before realizing its a genuine typo that does it and a simple fix takes a second -- but I would really have expected you to take some time and notice the striking absence of the parentheses within roughly 5 seconds of evaluation.

EDIT: Helpful note: if a compiler -or indeed, any kind of tool related to programming- complains about missing symbols it means you made a typo or forgot to import those symbols (typically pieces of library code). A compiler basically treats any program as a sequence of &#8216;things&#8217; that it calls &#8216;symbols&#8217; but most humans would probably call &#8216;names&#8217; because 95% of the time that is what they are. However, symbols extend beyond names -- they include any piece of syntax (such as &#8216;keywords&#8217; and &#8216;operators&#8217; -- even including parentheses).

Similarly &#8216;invalid&#8217; or &#8216;symbol not allowed here&#8217; or &#8216;syntax errors&#8217; problems mean that you are sure typing something but it is not this formal programming language as known by the compiler/tool.

---

### Post by pbrockway2 on 2009-10-17
So look at the symbol that the compiler is telling you about.

Look it up in the API documentation.  Have you spelt it correctly?  Is the cApItAlIsAtIoN correct?  If it is a method, does it have the right number of arguments (of the right sort and in the right order)?

---

### Post by s3a on 2009-10-17
Which parentheses? I still can't see my mistake. I did not know that when the compiler complains about symbols that the problem is usually a typo...that is useful advice so thanks for that but I'm still unable to spot my mistake.

---

### Post by pbrockway2 on 2009-10-17
> **s3a said:**
> Which parentheses?

The parentheses that aren't there! ;)

nextDouble is a method, right?  So...

---

### Post by s3a on 2009-10-17
Oh, I get it now! I can't believe I didn't see that! Thanks to all of you!

---

