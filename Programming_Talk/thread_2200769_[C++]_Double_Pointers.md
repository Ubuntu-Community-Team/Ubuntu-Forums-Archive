---
title: "[C++] Double Pointers?"
date: 2014-01-21
forum: Programming Talk
---

### Post by slooksterpsv on 2014-01-21
Hi all I have a question:

My game creates a **new** game object and passes the SDL_Renderer everywhere image handling, processing to the screen, etc. needs to be done. While this is fine I was wondering if it's possible to do something like the following:

```

Game* gameInst = new Game(640,480);
...

Game** gameObject;

...

void Editor::OnInit(Game* game)
{
 gameObject = &game;
}

...

Editor* editor = new Editor();

editor->OnInit(&gameInst);
...

```

To pass around the data. Would this be feasible  or not?

---

### Post by spjackson on 2014-01-21
It is possible with```

void Editor::OnInit(Game** game)
{
  gameObject = game;
}

```

---

