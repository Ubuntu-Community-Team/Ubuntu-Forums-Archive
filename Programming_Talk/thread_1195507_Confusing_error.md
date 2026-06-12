---
title: "Confusing error"
date: 2009-06-23
forum: Programming Talk
---

### Post by Thesuperchang on 2009-06-23
So this method is causing me relentless turmoil! What it's supposed to do is return the value of a colour requested by the user to draw with in the X Window System. If the colour exists, it will locate it in the colour array and return the colour value. If the colour has yet to be invented, the program will make the colour and return the newly made colour.

At the moment it seg. faults whenever a new colour is drawn with. It also seems to have a hard time locating the colours that already exist. I was thinking that it might be a simple bug which I may have overlooked so that is why I'm posting it here.

[PHP]colour_t& Colour(uint8_t red, uint8_t green, uint8_t blue) {
	int       index;
	colour_t *temp;

	if(colourCount == 0) {
		// Invent a new colour
		colourCount = 1;
		multiColour = (colour_t *)malloc(sizeof(colour_t) * colourCount );
		if(multiColour == NULL) {
			// Freak out!
		}
		index = colourCount;
		RequestColour(red, green, blue, (multiColour[index]));
		return multiColour[index];
	}			
	else {
		// Look for a match
		for(index = 0; index < (colourCount+0); index++) {
			if( (multiColour[index].colourID.red   == red)   &&
                            (multiColour[index].colourID.green == green) &&
                            (multiColour[index].colourID.blue  == blue) ) {
				return multiColour[index];
			}
		}
	
		// No match
		// Invent a new colour
		colourCount += 1;
		temp = multiColour;
		multiColour = (colour_t *)realloc( (void *)multiColour, sizeof(colour_t) * (colourCount + 0) );
		if(multiColour == NULL) {
			multiColour = temp;
		}
		index = colourCount;
		RequestColour(red, green, blue, (multiColour[index - 1]));
		return multiColour[index];
	}
}[/PHP]

Cheers,
C. Anderson

---

### Post by monraaf on 2009-06-23
> **Thesuperchang said:**
> 
At the moment it seg. faults whenever a new colour is drawn with. It also seems to have a hard time locating the colours that already exist. I was thinking that it might be a simple bug which I may have overlooked so that is why I'm posting it here.

[PHP]
	if(colourCount == 0) {
		// Invent a new colour
		colourCount = 1;
		multiColour = (colour_t *)malloc(sizeof(colour_t) * colourCount );
		if(multiColour == NULL) {
			// Freak out!
		}
		index = colourCount;
		RequestColour(red, green, blue, (multiColour[index]));
		return multiColour[index];
[/PHP]

You are creating 1 color here, but you are returning color nr.2 which does not exist, same at the end. Remember indexes start at 0.

---

### Post by Thesuperchang on 2009-06-23
> **monraaf said:**
> You are creating 1 color here, but you are returning color nr.2 which does not exist, same at the end. Remember indexes start at 0.

Spot on. The program no longer seg. faults. Thank you very much. Now the next issue is with finding duplicate colours within the array.

---

### Post by Thesuperchang on 2009-06-23
> **Thesuperchang said:**
> Spot on. The program no longer seg. faults. Thank you very much. Now the next issue is with finding duplicate colours within the array.

Problem resolved. I forgot to assign the values red, green and blue to the values I use to search.

---

### Post by Can+~ on 2009-06-23
Next time: use a Debugger

---

