---
title: "problem with nextLine() method in java..."
date: 2009-03-09
forum: Programming Talk
---

### Post by Mia_tech on 2009-03-09
guys, I'm implementing this code that takes in attributes from a product, by my first scan is jumping to the next line, not giving me an opporunity to enter the name for the description and jumping straight to price....but if I use the next() method, then the string can take only one word... and I would like to enter things like "Pepsi Cola".... any help appreciated

```
System.out.println("Description:");
String description = myscan.nextLine();
System.out.println("Price:");
double price = myscan.nextDouble();
System.out.println("Quantity:");
int qty = myscan.nextInt();
vm.addProduct(new Product(description, price, qty));
```

---

### Post by kavon89 on 2009-03-09
I really hate Scanner and I remember a thread about a month ago with an issue like this. [Here is the thread]("http://ubuntuforums.org/showthread.php?t=1068267") and one of the solutions was to try using this for your Scanner if you aren't already:

```
Scanner input = new Scanner(new BufferedReader(
    new InputStreamReader(System.in)).readLine());
```

---

### Post by Mia_tech on 2009-03-09
I used that line, but that threw an exception which made me add a "try catch"... but when run the app, nothing happens

---

### Post by andrew222 on 2009-03-09
Try this out to get the input


```
Scanner console = new Scanner(System.in);
String description = console.next();
String price = console.next();
double pr = Double.parseDouble(price);
String quantity = console.next();
int qty = Integer.parseInt(quantity);

```

---

