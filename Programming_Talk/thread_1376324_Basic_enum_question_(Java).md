---
title: "Basic enum question (Java)"
date: 2010-01-09
forum: Programming Talk
---

### Post by s3a on 2010-01-09
Here is my simplistic incomplete program:
```
public class GraphicsInformation
{
	public static void main (String[] args){
		for(GraphicCards Card: GraphicCards.values()){
			System.out.printf("%s %s \n", Card, Card.getVideoRAM());
		}
	}
}
```

```
public enum GraphicCards
{
	HD4850("512/1024"),
	N8800GTS("320/512");
	
	//private int weirdNumber; // find out real name
private String videoRAM;
	
GraphicCards(String videoRam){
	this.videoRAM = videoRAM;
}
public String getVideoRAM(){
	return videoRAM;
}

}
```

_My question is:_ **Why is it printing out null twice?**

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by raffaele181188 on 2010-01-09
My guess is that you mispelled in the constructor:
```

this.videoRAM = videoRAM;

```
while the parameter name is "videoRam" (note RAM/Ram), so it is assigned its automatic-set value null ;) There are no errors in your code, this works for me:
```

package rs18.enumtest;

public class Main {

    public enum GraphicCard {
        NVIDIA("1024MB"),
        INTEL("1024MB"),
        ATI("1024MB");

        public String ram = "";

        GraphicCard(String videoRAM) {
            this.ram = videoRAM;
        }
    }

    public static void main(String[] args) {
        for (GraphicCard card : GraphicCard.values())
            System.out.printf("%s: %s video RAM%n", card, card.ram);
    }

}

```
Since you seem new to Java, please follow Java coding guidelines about member case and other things :D

---

### Post by s3a on 2010-01-13
Sorry for the late response (Just came back to this thread now) and thanks for catching my typo. It solved my issue. :)

---

