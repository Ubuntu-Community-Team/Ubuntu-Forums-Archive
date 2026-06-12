---
title: "Property/filtered searches - how do *you* do them?"
date: 2008-07-12
forum: Programming Talk
---

### Post by Asham on 2008-07-12
Hello, it's me again. :-)

Property/filtered searches - how do *you* do them?

*I am a Java programmer but can follow code in C++, C#, python*


Hypothetical example: 
we own a car shop where you can search for cars by
	- brand name
	- model name
	- year
	- engine
	- gearbox
	- tires
	- rims
	- color
	- [et cetera]
	
So now the question is howto structure the DAO/DAO helper class in a well structured manner.

At first one could come up with a quick solution such as
```
List<Car> getCars(String brand, String model, String rims, String tires, String engine [and so on])
```
but this does not look efficient when we want to search for let's say just two attributes. Then we'd have to pass null arguments for properties we aren't going to search for, or to create a method for when searching for one attribute, another method for two attributes and so on. What if we were to remove an attribute from the search function?? :(
No, this is no viable way to go!

Another possibility could be to pass a Map of filters, such as
```
Map<String, String> filters = new LinkedHashMap<String, String>();
filters.put("brand", "Ford");
filters.put("model", "Falcon Futura");

List<Car> items = carDAO.getCars(filters);
```

Is this better? Yes, but not perfect either because we would have to memorize what filters that are searchable. That we can fix easily by adding an enum of search constants. We are also tied to using string objects. 


Another way could be to implement the command pattern, and perhaps append filters to the command before it's executed.

What are your thoughts? 

*I am a Java programmer but can follow code in C++, C#, python*

/Adam

---

### Post by LaRoza on 2008-07-12
This looks like a job for a database and SQl!

---

### Post by Asham on 2008-07-13
Yes, a database server is involved. However I am not there yet; at this point I'm trying to figure out a solid way to layer the application logic.

---

### Post by CptPicard on 2008-07-13
I know this is not going to be helpful, but...

[http://gigamonkeys.com/book/practical-a-simple-database.html](http://gigamonkeys.com/book/practical-a-simple-database.html)

Just shows that yes, there really is a reason to use higher-level languages...

---

### Post by archivator on 2008-07-13
This is a rather unorthodox solution (largely inspired by Django, btw) but I think it might work. 

The way I'd do it in any high-level language where the overhead is not really a problem involves using a SearchContext. 

I think code would be much better than verbal explanation, so: 
```
search = SearchContext().filter("rims", "big").filter("color", "epilepsy test")
search.execute()
```

The way I see it, instantiating a SearchContext() makes it enfold the entire database. Each subsequent call to filter() narrows down the scope. Obviously, filter() would need to return a reference to the same object so that the code is easier to read. Finally, execute() sends the SQL query and fills in an iterable data structure.

Internally, SearchContext() can store the filters in a variety of ways but an array of custom Filter objects looks like a good enough compromise.

On the data retrieval part, I think SearchContext() can easily be an iterable object itself once it's been execute()'d.

Again, this is pretty much the same thing Django does, only slightly more readable. It obviously has a pretty large overhead but on the other hand the code is readable and  highly extensible.

---

### Post by Phristen on 2008-07-13
> getCars(String brand, String model, String rims, String tires, String engine [and so on])Actually, you can do something like this instead:[php]
getCars (String ... filters) {
for (String filter : filters) {
// some code here
}
}
[/php]This method will accept an arbitrary number of parameters.

P.S.
On the second thought, this probably won't make your life any easier in this case...

---

### Post by txcrackers on 2008-07-13
I would actually recommend using a sparsely populated Car object in a query-by-example paradigm:
```

Car queryCar = new Car();
queryCar.setColor("Red");
queryCar.setDoors(2);
...
List<Cars> result = getCars(queryCar);

```
This ensures type-safety, you have complete control over the parameters and don't have to worry about someone using a wrong parameter name for the filter.

---

### Post by Asham on 2008-07-13
> **txcrackers said:**
> I would actually recommend using a sparsely populated Car object in a query-by-example paradigm:
```

Car queryCar = new Car();
queryCar.setColor("Red");
queryCar.setDoors(2);
...
List<Cars> result = getCars(queryCar);

```
This ensures type-safety, you have complete control over the parameters and don't have to worry about someone using a wrong parameter name for the filter.

This is essentially what you do when you work with Hibernate, an OR/Mapper. Wonder why I haven't thought of applying the same pattern here.. Looks like the code will get cleaner this way, at last!

I will try to find a good design patterns book. It's interesting, rewarding and fun to improve! Never thought I'd come to the day when I could actually see where improvements are needed. But here we are. Too bad I don't know how to implement  them :lolflag:


Thanks for all the input, guys! I'll read the links soon.

Feel free to add to the thread if you come up with anything new. 
/Adam

---

