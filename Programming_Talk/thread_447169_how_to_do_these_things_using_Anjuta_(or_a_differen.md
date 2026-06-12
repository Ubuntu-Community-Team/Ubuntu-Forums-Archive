---
title: "how to do these things using Anjuta (or a different C++ compiler)"
date: 2007-05-17
forum: Programming Talk
---

### Post by Fittersman on 2007-05-17
ok, im learning how to code still and ive been using a windows machine at school so far, so i dont know how to do some of hte things on ubuntu yet. what im trying to do is make a little game type thing sorta, ill include the code i have so far (its not a game yet, im just learning to make colors and shapes so far)

1) where to put the header files (i think thats what they are called i have two #include <Gui_bot.h> and #include <Gui_top.h> )

2) im having build problems, but that could be because i dont have those files in yet

heres my code if you care to look:

```
#include <Gui_top.h> 

void Grass(int x, int y)
{
	SetColor(GREEN);
	SetThickness(1);
	Line(x,y, x+10, y-20);
	Line(x,y, x-10, y-20);
	Line(x-5, y, x+15, y-15);
}
//makes grass

void DrawCar(int x, int y)
{
	SetThickness(2);
	SetFillColor(GRAY);
	FilledCircle(x,y,10);
	FilledCircle((x + 35),y,10);
	SetFillColor(YELLOW);
	FilledRectangle((x - 10),(y - 20),(x + 45),(y - 2));
	gotoxy((x + 8),(y - 7));
	SetTextFont("Times New Roman");
	SetTextColor(BLACK);
	SetTextSize(13);
	DrawText("TAXI");
	FloodFill((x + 8),(y - 7));
}
//draws a car

void DrawBorder()
{
	SetColor(GREEN);
	int MaxX = GetMaxX() - 40;
	int MaxY = GetMaxY() - 40;
	
	for (int i = 0; i < MaxX ; i++)
	{
		SetPixel((20 + i), 20);
		SetPixel((20 + i), 21);
		SetPixel((20 + i), 22);
		SetPixel((20 + i), 23);
	}

	for (int i = 0; i < MaxX ; i++)
	{
		SetPixel((20 + i), MaxY - 40);
		SetPixel((20 + i), MaxY - 41);
		SetPixel((20 + i), MaxY - 42);
		SetPixel((20 + i), MaxY - 43);
	}

	for (int i = 0; i < MaxY - 60; i++)
	{
		SetPixel(20, (20 + i));
		SetPixel(21, (20 + i));
		SetPixel(22, (20 + i));
		SetPixel(23, (20 + i));
	}

	for (int i = 0; i < MaxY - 60; i++)
	{
		SetPixel(MaxX + 20, (20 + i));
		SetPixel(MaxX + 21, (20 + i));
		SetPixel(MaxX + 22, (20 + i));
		SetPixel(MaxX + 23, (20 + i));
	}

}

class GuiClass
{
public:
	GuiClass();
	void GuiMouseClick(int x, int y); //action if mouse clicked
	void GuiPaint(); //repaint the entire window
	string Title();
private:
	int LastX;
	int LastY;
	int LastX2;
	int LastY2;
	int NumClicks;
};

GuiClass::GuiClass()
{}
	
string GuiClass::Title()
{
return "A pretty sweet production by [me]";
}

void GuiClass::GuiMouseClick(int x, int y)
{
	LastX2 = LastX;
	LastY2 = LastY;
	LastX = x;
	LastY = y;
	NumClicks++;
}

void GuiClass:: GuiPaint()
{
	//Click circles
	SetColor(RED);
	SetFillColor(RED);
	FilledCircle(LastX, LastY, 10);
	SetColor(BLACK);
	SetFillColor(BLACK);
	FilledCircle(LastX2, LastY2, 10);
	gotoxy(10,20);
	DrawText("Clicked at (");
	DrawText(LastX);
	DrawText(",");
	DrawText(LastY);
	DrawText(")   Number of clicks: ");
	DrawText(NumClicks);
	
	//house
	SetColor(BLACK);
	SetThickness(2);
	Rectangle(100,100,200,200);
	Line(100,100,150,50);
	Line(150,50,200,100);
	
	//lawn
	for (int x = 30; x <= 300; x += 12)
	{
		Grass(x,215);
		Grass(x,230);
	}
	
	//windows and door
	SetColor(BLACK);
	SetThickness(1);
	SetFillColor(GRAY);
	FilledRectangle(120,120,140,140);
	FilledRectangle(160,120,180,140);
	FilledRectangle(135,160,165,200);
	SetColor(WHITE);
	
	//doorknob
	SetPixel(160,180);
	
	//sun
	SetFillColor(YELLOW);
	SetColor(YELLOW);
	FilledCircle(280,50,30);
	SetFillColor(ORANGE);
	FloodFill(150,110);
	SetFillColor(VIOLET);
	FloodFill(150,90);
	
	//dog house
	SetColor(BLACK);
	SetThickness(2);
	SetFillColor(ORANGE);
	FilledRectangle(250,200,300,170);
	Line(250,170,275,140);
	Line(300,170,275,140);
	SetFillColor(VIOLET);
	FloodFill(270,150);
	SetFillColor(BLACK);
	SetThickness(1);
	FilledRectangle(260,200,290,180);
	
	//car
	DrawCar(250,300);
	
	//Border
	DrawBorder();
}

#include <Gui_bot.h>
```

---

### Post by slavik on 2007-05-18
1. you have no 'main'
2. if you include a file after your code, the code will not know anything about anything in that include. :) (why are you including anything after all your code, it's useless there ... )
3. I am not sure what graphics library you are using

---

### Post by Fittersman on 2007-05-20
i really dont know, but that code is copied and pasted from school, and it worked perfectly fine there, and i dont know what graphics library im using either, lol

its really not that bad if i cant get it to work at home, i can just do it at school

---

### Post by slavik on 2007-05-20
because it seems like you are either using a specialised compiler at school or some 'bad' library.

as it stands, the code you pasted will not run on its own (there is no main() ) it won't link either.

---

### Post by Fittersman on 2007-05-20
o, alright guess this will have to stay at school then, thanks for the help though

---

