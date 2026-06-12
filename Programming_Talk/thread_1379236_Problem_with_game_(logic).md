---
title: "Problem with game (logic?)"
date: 2010-01-12
forum: Programming Talk
---

### Post by matmatmat on 2010-01-12
I am trying to make a game in C# with SdlDotNet like this:
> 
Produce a game that shows the player increasing numbers of items and asks them to spot which item appears only once

More specifically, your game must do the following:

Show lots of items on the screen, bouncing around. Every item should appear at least twice (it can appear three times, four times, or whatever), except one item, which should only appear once.
In the beginning, few items should be shown. For example, the player might see two apples, three bananas, two pineapples and a lemon. In this case, the lemon is the correct answer - it's the only item that appears once.

If the player gets the correct answer, the game should level up and show more items. Eventually, at level 5, the screen will be full of items, at which point the player wins.

If the player chooses the wrong item, the game should level down and show fewer items. Don't go below the starting level.

Each time the level changes, the screen should be cleared and a new set of items should be shown. The item that appears once will also be different, because it should be chosen randomly.

(this was taken from an exercise on a website.)

So far, I have:
```

using SdlDotNet.Core;
using SdlDotNet.Graphics;
using SdlDotNet.Input;
using System;
using System.Collections.Generic;
using System.Drawing;

namespace OddOneOut
{
	public class OddOneOut
	{
		Surface sfcGameWindow;
		Surface sfcBackground = new Surface ("media/background.png");
		Surface sfcOops = new Surface ("media/oops.png");
		Surface sfcLevelUp = new Surface ("media/levelup.png");

		List<Surface> CardTypes = new List<Surface> ();
		List<Card> Cards = new List<Card> ();

		int MaxNumber = 3;
		Random Rand = new Random ();

		const int winHeight = 768;
		const int winWidth = 1024;

		int maxnumofthings = 3;

		List<int> Directions = new List<int> ();
		int DirectionPos;

		int level = 1;
		
		public OddOneOut ()
		{
			sfcGameWindow = Video.SetVideoMode (winWidth, winHeight);
			
			CardTypes.Add (new Surface ("media/card_1.png"));
			CardTypes.Add (new Surface ("media/card_2.png"));
			CardTypes.Add (new Surface ("media/card_3.png"));
			CardTypes.Add (new Surface ("media/card_4.png"));
			CardTypes.Add (new Surface ("media/card_5.png"));
			CardTypes.Add (new Surface ("media/card_6.png"));
			CardTypes.Add (new Surface ("media/card_7.png"));
			CardTypes.Add (new Surface ("media/card_8.png"));
			
			for (int i = 0; i < 360; ++i) {
				if (i < 10)
					continue;
				if (i >= 350)
					continue;
				if (i > 80 && i < 100)
					continue;
				if (i > 170 && i < 190)
					continue;
				if (i > 260 && i < 280)
					continue;
				
				Directions.Add (i);
			}
			ShuffleList (Directions);
		}

		public void Run ()
		{
			CreateCards ();
			
			Video.WindowCaption = "Odd One Out";
			Events.Tick += new EventHandler<TickEventArgs> (Events_Tick);
			Events.Quit += new EventHandler<QuitEventArgs> (Events_Quit);
			Events.MouseButtonUp += new EventHandler<MouseButtonEventArgs> (Events_MouseButtonUp);
			Events.Run ();
		}

		void Events_Tick (object sender, TickEventArgs e)
		{
			Update (e.SecondsElapsed);
			Draw ();
		}

		void Update (float elapsed)
		{
			foreach (Card card in Cards) {
				double xmove = (Math.Cos (card.Direction * Math.PI / 180) * card.Speed) * elapsed;
				double ymove = (Math.Sin (card.Direction * Math.PI / 180) * card.Speed) * elapsed;
				
				// these next two lines convert the doubles to floats
				card.X += Convert.ToSingle (xmove);
				card.Y += Convert.ToSingle (ymove);
				
				if (card.X > winWidth) {
					card.X = -CardTypes[0].Width;
				} else if (card.X < -CardTypes[0].Width) {
					card.X = winWidth;
				}
				
				if (card.Y > winHeight) {
					card.Y = -CardTypes[0].Height;
				} else if (card.Y < -CardTypes[0].Height) {
					card.Y = winHeight;
				}
			}
		}

		void Draw ()
		{
			sfcGameWindow.Blit (sfcBackground);
			
			foreach (Card card in Cards) {
				// the next line has been broken across two lines
				sfcGameWindow.Blit (CardTypes[card.Type], new Point (Convert.ToInt32 (card.X), Convert.ToInt32 (card.Y)));
			}
			
			sfcGameWindow.Update ();
		}

		void CreateCards ()
		{
			Cards.Clear ();
			
			int special = Rand.Next (0, MaxNumber);
			int numofthings;
			
			for (int i = 0; i < MaxNumber; i++) {
				if (i == special - 1) {
					CreateCard (i, true);
				} else {
					numofthings = Rand.Next (2, maxnumofthings);
					for (int y = 0; y <= numofthings; y++) {
						CreateCard (i, false);
					}
				}
			}
			MaxNumber++;
			if (MaxNumber == 4 || MaxNumber == 7 || MaxNumber == 8) {
				maxnumofthings++;
			}
		}

		void CreateCard (int i, bool y)
		{
			Card card = new Card ();
			
			card.X = Rand.Next (winWidth);
			card.Y = Rand.Next (winHeight);
			card.Speed = Rand.Next (70, 120);
			card.Type = i;
			card.Direction = ChooseCardDirection ();
			
			if (y) {
				card.special = true;
			} else {
				card.special = false;
			}
			
			Cards.Add (card);
		}

		int ChooseCardDirection ()
		{
			++DirectionPos;
			if (DirectionPos == Directions.Count)
				DirectionPos = 0;
			return Directions[DirectionPos];
		}

		void Events_MouseButtonUp (object sender, MouseButtonEventArgs e)
		{
			for (int i = 0; i < Cards.Count; ++i) {
				Card c = Cards[i];
				
				Rectangle mouse_rect = new Rectangle (Mouse.MousePosition.X, Mouse.MousePosition.Y, 64, 64);
				
				Rectangle card_rect = new Rectangle (Convert.ToInt32 (c.X), Convert.ToInt32 (c.Y), 64, 64);
				
				if (card_rect.IntersectsWith (mouse_rect)) {
					ClickCard (c);
				}
			}
		}

		void ClickCard (Card c)
		{
			if (c.special) {
				level++;
				Console.WriteLine(level);	
				
				sfcGameWindow.Blit (sfcLevelUp);
				sfcGameWindow.Update ();
				SdlDotNet.Core.Timer.DelaySeconds (2);
				CreateCards ();
			} else {
				Console.WriteLine(level);	
				
				sfcGameWindow.Blit (sfcOops);
				sfcGameWindow.Update ();
				if (level > 1) {
					MaxNumber--;
					level--;
				}
				if (MaxNumber == 3 || MaxNumber == 6 || MaxNumber == 7) {
					maxnumofthings--;
				}
				SdlDotNet.Core.Timer.DelaySeconds (2);
				CreateCards ();
			}
		}

		void Events_Quit (object sender, QuitEventArgs e)
		{
			Events.QuitApplication ();
		}



		void ShuffleList<T> (List<T> list)
		{
			for (int i = 0; i < list.Count; i++) {
				T tmp = list[i];
				list.RemoveAt (i);
				list.Insert (Rand.Next (0, list.Count), tmp);
			}
		}
	}
}

```

I have this bit of code that is causing the trouble:
```

		void ClickCard (Card c)
		{
			if (c.special) {
				level++;
				Console.WriteLine(level);	
				
				sfcGameWindow.Blit (sfcLevelUp);
				sfcGameWindow.Update ();
				SdlDotNet.Core.Timer.DelaySeconds (2);
				CreateCards ();
			} else {
				Console.WriteLine(level);	
				
				sfcGameWindow.Blit (sfcOops);
				sfcGameWindow.Update ();
				if (level > 1) {
					MaxNumber--;
					level--;
				}
				if (MaxNumber == 3 || MaxNumber == 6 || MaxNumber == 7) {
					maxnumofthings--;
				}
				SdlDotNet.Core.Timer.DelaySeconds (2);
				CreateCards ();
			}
		}

```
this code is called when the player clicks on the card, it then increase the number of tiles shown and level if it is the correct one, otherwise it decrease the number of cards shown and the level. 

Problem:
When going down a level it doesn't seem to decrease the numofthings and MaxNumber variables (that is - there always seems to be a lot more on the screen then there should be).

Could anybody give me an idea of why this is happening?

---

