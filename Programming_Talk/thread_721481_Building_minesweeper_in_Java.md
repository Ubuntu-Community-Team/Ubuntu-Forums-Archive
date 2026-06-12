---
title: "Building minesweeper in Java"
date: 2008-03-11
forum: Programming Talk
---

### Post by Fixel on 2008-03-11
Hi, I'm currently building a minesweeper game as a school project and I need some help. I didn't completely use English variables, some are in Swedish.

When running it I run into this error message:

```
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: 10
	at Minesweeper.minefield(Minesweeper.java:19)
	at Minesweeper.main(Minesweeper.java:10)

```

Here's the source code:

```
import javax.swing.*;

class Minesweeper{
	public static void main(String[] arg){
		JOptionPane.showMessageDialog(null, "Nu ska du få spela MineSweeper!");
		//först måste vi skapa ett 10x10 fält med cirka 15 minor
		String[][] v = new String[10][10];
		int[][] b = new int[10][10];
		int räknare = 100;
		minefield(v, b, räknare);
		indexer(v);
		printer(v);
		game(v, b, räknare);
	}
	public static void minefield(String v[][], int b[][], int räknare){
		for(int i=0; i<=10; i++){
			for(int j=0; j<=10; j++){
				if((int)(Math.random()*10) == 2){
					v[i][j] = "¤";
					b[i][j] = -1;
					räknare -= 1;
				}
			}
		}
	}
	public static void printer(String v[][]){
		
		for(int i=0; i<=10; i++){
			for(int j=0; j<=10; j++){
				System.out.print(" " + v[i][j]);
			}
			System.out.println();
		}
	}
	public static void game(String v[][], int b[][], int räknare){
		String[][] spelarensvy = new String[10][10];
		for(int x=0; x<=10; x++){
			for(int z=0; z<=10; z++){
				spelarensvy[x][z] = "[]";
			}
		}
		
		String namn = JOptionPane.showInputDialog(null, "Skriv in ditt spelarnamn: ");
		JOptionPane.showMessageDialog(null, "Spelet förutsätter att du kan spela Minesweeper.\nMinor indikeras med -1");
		boolean goOn = false;
		while(goOn){
			gameprinter(spelarensvy, namn);
			String xinput = JOptionPane.showInputDialog(null, "Skriv in X-kord");
			int xcord = Integer.parseInt(xinput);
			String yinput = JOptionPane.showInputDialog(null, "Skriv in X-kord");
			int ycord = Integer.parseInt(yinput);
			if(b[xcord][ycord] == -1){
				JOptionPane.showMessageDialog(null, "Game Over");
				goOn = true;
			}
			else{
				spelarensvy[xcord][ycord] = v[xcord][ycord];
			}
		}
		System.exit(0);
	}
	public static void gameprinter(String[][] spelarensvy, String namn){
		System.out.println();
		System.out.print(namn);
		for(int p=0; p<=(41-namn.length()); p++)
			System.out.print("-");
		System.out.println("------------------------------------------");
		System.out.println("Y:");
		for(int i=0; i<=10; i++){
			System.out.print(i + "   ");
			for(int j=0; j<=10; j++){
				System.out.print(spelarensvy[i][j]);
			}
		}
		System.out.println("------------------------------------------");
		System.out.println("X:  1   2   3   4   5   6   7   8   9   10");
	}
	
	public static void indexer(String v[][]){
		
		for(int i=0; i<=10; i++){
			for(int j=0; j<=10; j++){
				int counter = 0;
				if(v[i][j] == "¤")
					break;
				// top left
				if(v[i-1][j-1] == "¤")
					counter += 1;
				// top middle
				if(v[i-1][j] == "¤")
					counter += 1;
				// top right
				if(v[i-1][j+1] == "¤")
					counter += 1;
				// middle right
				if(v[i][j-1] == "¤")
					counter += 1;
				// middle left
				if(v[i][j+1] == "¤")
					counter += 1;
				// bottom middle
				if(v[i+1][j] == "¤")
					counter += 1;
				// bottom left
				if(v[i+1][j-1] == "¤")
					counter += 1;
				// bottom right
				if(v[i+1][j+1] == "¤")
					counter += 1;
				String counter_int = Integer.toString(counter);
				v[i][j] = counter_int;
			}
		}
	}

}

```

This is my first time writing a game, so I'm kind of improvising.. and also since I don't know how to make a proper GUI I'm using the CMD-prompt to draw up the game board. Since I get an error I can't really see what I need to correct for it to look good, please bear with me. :)

Also, how do you make eclipse show the row number? Incredibly irritating to not have that feature around. ^^

---

### Post by Zugzwang on 2008-03-11
Well, the exception says what it says: Your arrays are too small.

If you write
```
int[] a = new int[10];
```
then your array "a" has storage space for precisely 10 elements (as the command suggests), namely a[0], a[1], a[2], a[3], a[4], a[5], a[6], a[7], a[8], a[9]. You can see that there is no a[10] - Trying to access is results in such an exception. This is because if there was, then you would have 11 elements in the array which isn't what you specified. However, you have loops:
[PHP]
for(int i=0; i<=10; i++){
   for(int j=0; j<=10; j++){
      System.out.print(" " + v[i][j]);
   }
   System.out.println();
}
[/PHP]
which *do* access the 10th elements of the (2D) array.

---

### Post by Fixel on 2008-03-11
Ok, fixed that issue, now the if's I've placed in the last method are letting me check the spaces for mines next to them. But when I get to the edge of my array it goes out of range. What should I do to look for mines? 

The purpose of that method is to place out the numbers that appear when you've pressed a button close to a mine (or several).

---

### Post by Zugzwang on 2008-03-11
Well, you will have to do range checks before trying to access a place on the field (e.g. only look for a mine right of a position if its x-coordinate is < 9).

Alternatively, place a *try {...} catch (ArrayIndexOutOfBoundsException e) { /* Safe to discard */} * around each block of the form:
```

if(v[i][j+1] == "¤")
   counter += 1;

```
However, this is considered to be *very* bad style (other possible disadvantages are not mentioned here). You should stick with the first way.

---

### Post by Fixel on 2008-03-11
Ok, fixed the loops, but now the last method (indexer) is still f:ed, what do you mean with range checks? Just a simple if-check?

---

### Post by Fixel on 2008-03-11
Ok decided to try the if's... this is the result:

```
 ¤ null null null null null null ¤ null null
 1 1 1 1 1 0 2 ¤ null null
 0 0 1 ¤ null null null null null null
 0 0 1 1 1 0 0 1 ¤ null
 0 0 0 0 0 0 0 2 2 2
 0 0 0 1 2 2 1 1 ¤ null
 0 0 0 2 ¤ ¤ null null null ¤
 1 1 1 2 ¤ null null ¤ null ¤
 1 ¤ null null null null null null ¤ null
 1 1 1 0 0 1 ¤ null null null
```

The last method now looks like this:

```
	public static void indexer(String v[][], int b[][]){
		
		for(int i=0; i<v.length; i++){
			for(int j=0; j<v.length; j++){
				int counter = 0;
				if(v[i][j] == "¤")
					break;
				// top left
				if(i-1 >= 0 && j-1 >= 0){
					if(v[i-1][j-1] == "¤")
						counter += 1;
				}
				// top middle
				if(i-1 >= 0){
					if(v[i-1][j] == "¤")
						counter += 1;
				}
				// top right
				if(i-1 >= 0 && j+1 <= 9){
					if(v[i-1][j+1] == "¤")
						counter += 1;
				}
				// middle right
				if(j-1 >= 0){
					if(v[i][j-1] == "¤")
						counter += 1;
				}
				// middle left
				if(j+1 <= 9){
					if(v[i][j+1] == "¤")
						counter += 1;
				}
				// bottom middle
				if(i+1 <= 9){
					if(v[i+1][j] == "¤")
						counter += 1;
				}
				// bottom left
				if(i+1 <= 9 && j-1 >= 0){
					if(v[i+1][j-1] == "¤")
						counter += 1;
				}
				// bottom right
				if(i+1 <= 9 && j+1 <=9){
					if(v[i+1][j+1] == "¤")
						counter += 1;
				}
				b[i][j] = counter;
				String counter_int = Integer.toString(counter);
				v[i][j] = counter_int;
			}
		}
	}

}
```

---

