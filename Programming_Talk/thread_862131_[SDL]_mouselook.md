---
title: "[SDL] mouselook"
date: 2008-07-17
forum: Programming Talk
---

### Post by Sockerdrickan on 2008-07-17
Hi I can't get mouselook working it's been bugging me off for hours

```
void MouseUpdate() {
    static int old_x, old_y;
    int x, y;
    SDL_GetRelativeMouseState(&x,&y);

    CamYaw+=x;
    CamPitch+=y;

    old_x=x;
    old_y=y;

    if(CamPitch<-90)
        CamPitch=-90;

    if(CamPitch>90)
        CamPitch=90;

    SDL_WarpMouse(r_width/2,r_height/2);
}
```

I don't know where to use old_x and old_y :mad:

---

### Post by hod139 on 2008-07-17
SDL_GetRelativeMouseState sets x and y to the change in mouse position since the last call to SDL_GetRelativeMouseState.  What you are setting old_x and old_y to is actually the change in x and change in y.

---

### Post by Sockerdrickan on 2008-07-17
fixed

```
void MouseUpdate() {
    int x, y;
    SDL_GetMouseState(&x,&y);
    SDL_WarpMouse(r_width/2,r_height/2);

    CamYaw+=(x-r_width/2)*0.2;
    CamPitch+=(y-r_height/2)*0.2;

    if(CamPitch<-90) {
        CamPitch=-90;
    }

    if(CamPitch>90) {
        CamPitch=90;
    }
}
```

---

