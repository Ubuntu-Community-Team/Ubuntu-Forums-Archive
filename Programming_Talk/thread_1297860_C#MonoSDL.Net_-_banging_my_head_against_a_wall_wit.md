---
title: "C#/Mono/SDL.Net - banging my head against a wall with simple algorithm."
date: 2009-10-22
forum: Programming Talk
---

### Post by dchurch24 on 2009-10-22
Hi all,

I am trying to build a dynamic 'grid' of sprites - these are 'shaded buttons' for a user to click on.

I'm using C#/SDL, although the coding is not the problem. The problem is I have a nested loop (x and y), the y being an array of y co-ords - there's a reason for this, although I'm open to suggestions to other ways to do the same.

The problem is, that although it DOES draw a grid of 20 sprites (5x4), sprites 2,3 & 4 never show up. I have outputted the x and y co-ords to the console, and they look fine. They just don't show.

```


private void drawButtons()
        {
            m_VideoSurface = Video.SetVideoMode(1024, 768, false, false, false);
            int prevX = 205;
            int[] ytop;
            ytop = new int[10];
            ytop[1] = 30;
            ytop[2] = 142;
            ytop[3] = 254;
            ytop[4] = 366;

            int butCnt = 0;

            for (int yo = 1; yo < 5; yo++)
            {
                for (int i = 1; i < 6; i++)
                {
                    butCnt++;
                    sb[butCnt] = new Sprite("blue_button.jpg");
                    sb[butCnt].X = prevX + 133;                    
                    sb[butCnt].Y = ytop[yo] - 10;  
                    sb[butCnt].Z = -1;
                    prevX = sb[butCnt].X;
                }
                prevX = 205;
                sb[yo].Y = ytop[yo] - 10;
            }
        }

private void Events_TickEvent(object sender, TickEventArgs e)
        {
            try
            {
                Video.Screen.Fill(Color.Black);
                for (int q = 1; q < 21; q++)
                {
                    Video.Screen.Blit(sb[q]);                    
                }
                Video.Screen.Update();
            }
            catch(Exception ex)
            {
                Console.WriteLine(ex.ToString());
            }            
        }


```

---

### Post by dchurch24 on 2009-10-22
I've just changed the code to include another Sprite object, and that one displays where I would expect it to.

This is getting very odd!

```

private void drawButtons()
        {
            m_VideoSurface = Video.SetVideoMode(1024, 768, false, false, false);
            int prevX = 205;
            int[] ytop;
            ytop = new int[10];
            ytop[1] = 30;
            ytop[2] = 142;
            ytop[3] = 254;
            ytop[4] = 366;

            SpriteCollection sc = new SpriteCollection ();

            int butCnt = 0;
            f = new SdlDotNet.Graphics.Font("browau.ttf", 28);

            for (int yo = 1; yo < 5; yo++)
            {
                for (int i = 1; i < 6; i++)
                {
                    butCnt++;
                    sb[butCnt] = new Sprite("blue_button.jpg");
                    sb[butCnt].X = prevX + 133;                    
                    sb[butCnt].Y = ytop[yo] - 10;  
                    sb[butCnt].Z = -1;

                    if (sCmdTitle[butCnt] != null)
                    {
                        sbText[butCnt] = new Sprite(f.Render(sCmdTitle[butCnt], Color.White));
                    }
                    else
                    {
                        sbText[butCnt] = new Sprite(f.Render("Nothing", Color.White));
                    }
                    sbText[butCnt].X = prevX + 133;
                    sbText[butCnt].Y = ytop[yo] - 10;
                    sbText[butCnt].Z = -1;

                    sc.EnableMouseButtonEvent();
                    sc.Add (sb[butCnt]);
                    prevX = sb[butCnt].X;
                }
                prevX = 205;
                sb[yo].Y = ytop[yo] - 10;
            }
        }
        private void Events_TickEvent(object sender, TickEventArgs e)
        {
            try
            {
                Video.Screen.Fill(Color.Black);
                for (int q = 1; q < 21; q++)
                {
                    Video.Screen.Blit(sb[q]);
                    Video.Screen.Blit(sbText[q]); 
                }
                Video.Screen.Update();
            }
            catch(Exception ex)
            {
                Console.WriteLine(ex.ToString());
            }            
        }
        private void OnMouseButtonDown(object sender, MouseButtonEventArgs e)
        {
            for (int cmds = 1; cmds < 21; cmds++)
            {
                if (this.sb[cmds].IntersectsWith(new Point(e.X, e.Y)))
                {
                    Console.WriteLine(sCmd1[cmds]);
                }
            }
        }

```


EDIT: Found it! 

"sbText[butCnt].Y = ytop[yo] - 10;"

I don't know what I thought I was doing with that line - must have had a late night or something!

---

