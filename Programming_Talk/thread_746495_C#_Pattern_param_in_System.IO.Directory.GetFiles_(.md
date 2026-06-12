---
title: "C# Pattern param in System.IO.Directory.GetFiles ()"
date: 2008-04-05
forum: Programming Talk
---

### Post by Jordanwb on 2008-04-05
I'm using Mono of my laptop and I have a question about the method System.IO.Directory.GetFiles (). In windows if I want to search for a jpeg I do: "*.jpg" and it returns all the jpg's in the specified dir. However this doesn't work in Linux. What would be the equivalent?

Also how do I do TypeParams in C#.Mono (as I refer to it)?

---

### Post by luisromangz on 2008-04-05
I have just tested it and it works in Mono in Gutsy Gibbon perfectly. Maybe the differnce is that in Windows, the case of the filename doesn't matter, but in linux it does.

---

### Post by Jordanwb on 2008-04-05
I was doing to following:

System.IO.File.Delete (dir + file); Passed in /home/jordanwb/Music/home/jordanwb/Music/3 Doors Down/filename.jpg

instead of

System.IO.File.Delete (file); Passed in /home/jordanwb/Music/3 Doors Down/filename.jpg

I keep forgetting that. do you know how to do typeparams like C#.Net's System.Collections.Generics.List does? IE:

List<stirng> list = new List<string> ();

---

### Post by luisromangz on 2008-04-05
To create a generic class you need to define your class as:

public class MyGenericClass<T>
{
  ....
}

And then you can use T as if it where a normal type where you want.

---

### Post by Jordanwb on 2008-04-05
MonoDevelop doesn't like TypeParams

public class HashMap <K, V>
{

}

---

