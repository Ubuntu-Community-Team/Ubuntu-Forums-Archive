---
title: "New Here But Need Some Help"
date: 2005-11-24
forum: Programming Talk
---

### Post by liviu chirila on 2005-11-24
im also an ubuntu linux user for almost a week an d i have to say thats its a very nice and good distro for my needs.

i didnt know were to post it but i need some help to make thse alghoritms in c/c++


1. struct Node {
	int Valoare;
	Node dreapta, stanga;
}

boolean IsInInterval(Node node, int min, int max)
begin
	return ((node-> Valoare  >= min) && (node-> Valoare  <= max));
end

procedure Visit(int min, int max, Node node)
begin
	if (node == null)				
then exit;
	if ((node-> Valoare  >= min) && (node-> Valoare  <= max)) /*interval*/
		then Print(node);
	if (node.info >= min)				
		then Visit(min, max, node->stanga);
	if (node.info <= max)				
		then Visit(min, max, node->dreapta);
end

2. Type 
	Q = class
		Min: Integer;
		AVL: TAVLTree
		function Minim: Integer;
		function Insert(Value: Integer): Integer;
	End;

function Q.Minim: Integer;
begin
	Result:= Min;
end;

function Q.Insert(Value: Integer): Integer;
begin
	if Value < Minim then
		Exit
	AVL.Insert(Value)
end

function Q.DeleteMin: Integer;
begin
   Result:= Minim; //Result = valoarea ce o va intoarce functia
   AVL.DeleteItem(Result); // se sterge valoarea minima
  Min:= AVL.MostLeftNode.Value
end;

3. Type Q = class
		Min, Max: Integer;
		Freq:Array[0..k] of Integer
		Next: Array[0..k] of Integer
		function Minim: Integer;
		function Insert(Value: Integer): Integer;
	End;

function Q.Minim: Integer;
begin
	Result:= Min;
end;

function Q.Insert(Value: Integer): Integer;
begin
	if Value < Minim then
		Exit
	Inc(Freq[Value]);
	//Daca Freq[Value] > 1, elementul mai exista deja, deci nu sunt necesare alte modificari
	if Freq[Value]>1 then		
		Exit;
	if (Max < Val)
		Next[Max] = Val
		Max = Val
		Exit
	//cautam valoarea imediat mai mica.
	MinLeft:= FindLowerValue(Value)
	Next[Value] = Next[MinLeft]
end

function Q.DeleteMin: Integer;
begin
	Dec(Freq[Min]);
	Result:= Min
		If Freq[Minim] > 0 then
		Exit;
	//Trebuie actualizat minimul
	if Min = Max then
		Min = -1;
	Min = Next[Min]
end;


p.s i need them to be made in c/c++ 10x a lot

---

### Post by bignate on 2005-11-25
You might get some help if you said what was working and what wasn't.

---

### Post by gord on 2005-11-26
and also put your code in [ code ] tags to preserve the formatting

---

### Post by otake-tux on 2005-11-28
you need to make it easier to follow your pseudo-code or you could post the code (well commented and formatted) and we will see how it goes.

---

