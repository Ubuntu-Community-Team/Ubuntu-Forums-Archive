---
title: "Mono and c# give compile error"
date: 2012-11-11
forum: Programming Talk
---

### Post by BluNova on 2012-11-11
I am learning Monogame (opensource xna implementation) and I am using a guide and im making a pong clone.

```
public Bat (ContentManager content, Vector2 screenSize, bool side)
        {
            moveSpeed = 6;
            points = 0;
            texture = content.Load&lt;Texture2D&gt;("bat");
            size = new Rectangle(0, 0, texture.Width, texture.Height);
            if (side)
            {
                position = new Vector2(30, screenSize.y / 2 - size.Height / 2);
            }
            else
            {
                position = new Vector2(screenSize.X - 30 - size.Width, screenSize.Y / 2 - size.Height / 2);
            }
        }

```

on the texture = content.Load&lt;Texture2d&gt;("bat");
I get errors on the &lt and &gt parts saying
> Only assignment, call, increment, decrement, and new object expressions can be used as a statement (CS0201)

And i don't see why it doesnt work i'm following a guide which says to type that and it just doesn't work

---

### Post by directhex on 2012-11-11
> **BluNova said:**
> I am learning Monogame (opensource xna implementation) and I am using a guide and im making a pong clone.

```
public Bat (ContentManager content, Vector2 screenSize, bool side)
        {
            moveSpeed = 6;
            points = 0;
            texture = content.Load&lt;Texture2D&gt;("bat");
            size = new Rectangle(0, 0, texture.Width, texture.Height);
            if (side)
            {
                position = new Vector2(30, screenSize.y / 2 - size.Height / 2);
            }
            else
            {
                position = new Vector2(screenSize.X - 30 - size.Width, screenSize.Y / 2 - size.Height / 2);
            }
        }

```

on the texture = content.Load&lt;Texture2d&gt;("bat");
I get errors on the &lt and &gt parts saying


And i don't see why it doesnt work i'm following a guide which says to type that and it just doesn't work

&gt; and &lt; are HTML character entities, allowing you to write reserved characters into a web page. Seems you made an error when copy-pasting your samples from the web.

Every &lt; should be <

Every &gt; should be >

---

