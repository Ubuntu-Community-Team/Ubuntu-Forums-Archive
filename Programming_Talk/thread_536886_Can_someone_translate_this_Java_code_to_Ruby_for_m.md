---
title: "Can someone translate this Java code to Ruby for me?"
date: 2007-08-28
forum: Programming Talk
---

### Post by the.dark.lord on 2007-08-28
```

import java.io.*;
public class harlinux
{
	public static void main(String[] args) throws IOException
	{
		for(int ctr=0;ctr<10;ctr++)
		{
			PrintWriter ofile = new PrintWriter(new BufferedWriter(new FileWriter(ctr+".txt")));
			ofile.println("hi");
			ofile.close();
		}
	}
}

```

Thanks a million in advance!! :)

---

### Post by Ramses de Norre on 2007-08-28
```
#!/usr/bin/env ruby

for i in (0..9) do
    file=File.new(i.to_s+".txt","w");
    file.puts "hi";
    file.close;
end


```

---

### Post by stylishpants on 2007-08-28
Ruby needs no semicolons.

```
#!/usr/bin/env ruby

(0 .. 9).each do |i|

    File.open("#{i}.txt","w") { |io| io.puts "hi" }

end
```

---

### Post by Ramses de Norre on 2007-08-28
I think semicolons are a rather good habit, even if it's not necessary. And closures are pretty abstract for a beginning programmer (which the OP probably is if he needs that code translated).

EDIT: since I actually am interested by these closures, is your code the same as this (I just wrote it to try and it feels logic to me):
```
#!/usr/bin/env ruby                                                                                       

(0..9).each do |i|
    File.new("#{i}.txt","w").puts "hi";
end

```

---

### Post by stylishpants on 2007-08-28
> **Ramses de Norre said:**
> 
EDIT: since I actually am interested by these closures, is your code the same as this (I just wrote it to try and it feels logic to me):
```
#!/usr/bin/env ruby                                                                                       

(0..9).each do |i|
    File.new("#{i}.txt","w").puts "hi";
end

```

Yes, my code is the same as that, except that in my code -- like in your original code -- the filehandle gets closed afterward. 

I used File.open because File.new won't take a closure.

---

### Post by Ramses de Norre on 2007-08-29
The closing is automatically done by the closure then?

---

### Post by stylishpants on 2007-08-29
The automatic closing is done because it is the documented behaviour of the  File::Open function when it's given a closure.

If you have the 'ri' package installed then you can see that documentation with this command: 
   ri IO::Open  (File inherits this method from the IO class.)

This is sort of thing is very common in ruby.  Anytime you deal with an object you can iterate through, a built-in iterator is provided, and you should use that built-in iterator and give it a closure.  All the little housekeeping details are then handled automatically.  

Closures are tricky and advanced in many language, but they are so basic, fundamental and common in ruby that they should be learned and used by beginners right away.

---

