---
title: "[Ruby] Command line arguments and input"
date: 2010-02-10
forum: Programming Talk
---

### Post by patrickaupperle on 2010-02-10
I was following a C# tutorial and came across a program. With my modifications, it looks like this
```
using System;
public class hello {
	public static void Main(string[] args) {
		Console.Write("What is your name? ");
		string name = Console.ReadLine();
		Console.WriteLine("Hello, {0}", name);
		Console.WriteLine("You entered the following {0} command line arguments:", args.Length );
//		for (int i=0; i < args.Length; i++)
//	        	Console.WriteLine("{0}", args[i]); 
		foreach (String arg in args)
			Console.WriteLine(arg);
	}
}
```

I was then trying to duplicate it in Ruby (even though I know little to nothing about ruby) and this is what I came up with:

```
#!/usr/bin/env ruby

print "What is your name? "
name = gets.chomp
puts "Hello, #{name}!"
puts "You entered the following #{ARGV.length} command line arguments:"
ARGV.each do|arg|
	puts "#{arg}"
end
```

And, because of some (proabably obvious) mistake I made, it does not work. It should ask for your name, print Hello, (your name), then tell you how many command line arguments you entered and what they are. Can someone correct this code?

---

### Post by stylishpants on 2010-02-11
The problem is where you say 'gets.chomp'.

Ruby doesn't know this 'gets' you are talking about.  Ruby on the whole doesn't tend to have many method names available in the global namespace, most of the time you call methods from objects.

In this case, you are trying to using the gets method of STDIN, which is made available in the constant STDIN and in the global variable $stdin.  Just include that object name and your code works.

```
#!/usr/bin/env ruby

print "What is your name? "
name = $stdin.gets.chomp
puts "Hello, #{name}!"
puts "You entered the following #{ARGV.length} command line arguments:"
ARGV.each do|arg|
	puts "#{arg}"
end
```

---

### Post by patrickaupperle on 2010-02-11
Thank you. I knew it would be something fairly simple. ;)

---

