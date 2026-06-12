---
title: "Call a variable from a string (Java)"
date: 2010-10-14
forum: Programming Talk
---

### Post by linux noooob on 2010-10-14
I wondered if it's possible to call a variable from a string value. for example:
```

ImageIconC=(newImageIcon(this.getClass().getResource("/C.jpeg")));
card=("C");
lblDisplay.setIcon(card);

```

That's the example even though I know it doesn't work like that. I am wondering if there is any code to turn that string into source code. Kind of like how Integer.parseInt changes string to integer values, is there any way to turn strings into source code have them read as if they where.

---

### Post by squaregoldfish on 2010-10-14
I believe you want to look into the Java Reflection API.

Steve.

---

### Post by linux noooob on 2010-10-14
So I guess your saying it's going to be more difficult then randomizing a number from 1-52 and using if statements to set each number to a card image to show. In all honesty I can't figure this reflection stuff out to make this work xD. Thanks for the reply though.

---

### Post by squaregoldfish on 2010-10-14
It sounds as though you'd be better of just having an array of 52 image objects pre-loaded in memory, then selecting the one you need by index.

Steve.

---

### Post by Reiger on 2010-10-14
It sounds like you are doing something typical of language like PHP:
[PHP]
function get_random_card() {
  $cards = get_an_array_of_cards();
  $random_key = get_a_random_key();
  return $cards[$random_key];
}
[/PHP]

Python:

```

def random_card():
  cards = get_card_dict()
  random_key = get_a_random_key()
  return cards[random_key]

```

But the equivalent Java thing to do is program something like this:

```

public class Card {
  /**
   * Creates &amp; sets up a {@link Card} based on a random 
   * integer index.
   * @param randomKey a random {@code int} value to map to an {@link Icon}.
   */
  public Card(int randomKey) {
    /* map randomKey to a resource name/file
  }

  /**
   * Get an {@link Icon} which corresponds to this {@link Card}.
   * @return an {@link Icon} which represents this {@link Card}.
   */
  public Icon getIcon() {
    /* return an ImageIcon here  */
  }
}

```

---

### Post by KdotJ on 2010-10-14
> **squaregoldfish said:**
> It sounds as though you'd be better of just having an array of 52 image objects pre-loaded in memory, then selecting the one you need by index.

Steve.

This is a much more preferred way of doing it. Using strings, converting then to varible names seems long winded and uneeded....

---

### Post by endotherm on 2010-10-14
what you are describing is called dynamic code. Java doesn't really support it per se but there is always a way to do it if you look at it from outside the code file. for instance, I need a set of dynamically defined classes generated at runtime for one of my apps. so I wrote a little cli app to generate the code, and insert the codefile into my project just before compilation. visual studio lets you run "Prebuild" commands (I'm sure eclipse/netbeans have simillar options) so each time I build, my data classes are regenerated based on my current schema, and I don't have to update them anymore.

---

### Post by Some Penguin on 2010-10-14
*shrug*  Really, if you wanted to associate arbitrarily strings with arbitrary values (which is what 'create a new variable whose name is a variable' really does in an interpreted language -- it's just another slot in the symbol table), you'd use a Map anyway.

And it could be arbitrary -- Map<String,Object> -- even.

However, this is usually not exactly a great way to structure code.  Use the array of (image names, image objects; depends upon storage/speed trade-off).

---

### Post by linux noooob on 2010-10-14
I want to do it this way because I would only need one line of code or close to it. Not 52 lines of code saying ```

ImageIcon CA=(newImageIcon(this.getClass().getResource("/CA.jpeg"))
if(cardType=1){
lblDisplay.setIcon(CA)

}
```

---

### Post by r-senior on 2010-10-14
Similar idea to a Map but could a Java 5 enumeration do a job for you here? Here's an example I had kicking around ...

```

...

public enum Region {
    
        NORTH_AMERICA(0, "N. America")
    ,   CENTRAL_AMERICA(1, "C. America")
    ,   SOUTH_AMERICA(2, "S. America")
    ,   AFRICA(3, "Africa")
    ,   EUROPE(4, "Europe")
    ,   MIDDLE_EAST(5, "Middle East")
    ,   EAST_ASIA(6, "N.E. Asia")
    ,   MAINLAND_ASIA(7, "S. Asia")
    ,   SOUTH_EAST_ASIA(8, "S.E Asia")
    ,   AUSTRALASIA(9, "Australasia")
    ,   OTHER(10, "Other")
    ;
    
    private Integer id;
    private String description;
    
    // Constructor of an enum is used to initialise the properties of
    // each enum value ...

    private Region(Integer id, String description) {
        this.setId(id);
        this.setDescription(description);
    }

    // Getters and setters ...
    
    public Integer getId() {
        return id;
    }

    public void setId(Integer id) {
        this.id = id;
    }
    
    public String getDescription() {
        return description;
    }

    public void setDescription(String description) {
        this.description = description;
    }
}

```

You can then write code like:

```

    Region region = Region.EUROPE;
    Region anotherRegion = Region.AFRICA;

    for (Region r : Region.values()) {
        System.out.println(r.getDescription());
    }

    ...

    if (region == Region.NORTH_AMERICA) {
       ...
    }


```

You need to use your imagination a bit to translate between this example of regions and your cards, but I could imagine a Card enum having an "image" property:

```

Card card = Card.ACE_OF_SPADES;
lblDisplay.setIcon(card.getImage());

```

I've not thought it through or played with any code. Just an idea?

---

### Post by linux noooob on 2010-10-15
So I decided on doing an array. Now I was going to randomize a number put it in a variable i and then use that to find the index of the array. But when I use this code 
```
  lblP1.setIcon(cards[i]);
``` it says that: ```
array required but java.util.ArrayList<javax.swing.ImageIcon> found 
```

---

### Post by squaregoldfish on 2010-10-15
Arrays of objects in Java don't work the same as arrays of primitive types (int, char etc), so using the [i] notation doesn't work. Instead, you have to use the API for an ArrayList. So, assuming your ArrayList is called cards, you use:

```
lblP1.setIcon(cards.get(i));
```

---

### Post by linux noooob on 2010-10-15
Now I used 
```
ArrayList<ImageIcon> cards = new <ImageIcon>ArrayList();
```

to initialize the array. Then I used
```
cards.add(newImageIcon(this.getClass().getResource("/C2.jpeg")));
``` 
to add the image files.

But there is an error in the program when it runs. It says i'm calling for index 1 but the size is zero. So how would I define the size of the array?

---

### Post by squaregoldfish on 2010-10-15
You don't need to define the size of an ArrayList - it will grow as required. You have to remember that all these things are zero-based, so your single added card will be at index zero.

Steve.

---

### Post by linux noooob on 2010-10-15
Figured it out (btw I have 52 cards in the array list) The problem is because the randomize is giving out a double value. I used ```
Math.round(i);
```
But since it's a double it is read at (for example) 5.0

Is there any way I can convert this to an integer?

---

### Post by squaregoldfish on 2010-10-15
There is, but I think we're in danger of writing the whole program for you. Try looking around for a bit...

Steve.

---

### Post by linux noooob on 2010-10-15
I'll look around. And I'm just asking things I would ask my teacher if they were online. I will look around for a bit I guess. Just pressed for time.

EDIT: I can see why you said that. Quick google search and I find i could do something like

 > i=(int)b;

---

### Post by linux noooob on 2010-10-15
Ok I don't know why but every time I generate an array list it randomizes the contents and the order their in!

---

