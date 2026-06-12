---
title: "Timers in SDL... o.O"
date: 2011-08-11
forum: Programming Talk
---

### Post by Ravenshade on 2011-08-11
Hi folks, 

I'm wondering who knows what about these things. Lots of places advise me to use SDL_GetTicks() but I...for some reason am finding it hard to figure out. I'm not even sure it would be suitable to use. 

My animation displays four images...basically along these lines. 

[PHP]
aria.get_map(world, display);
if (chest_01_front == false)
{
    apply_surface(9*square_size, 10*square_size, items, display);
}
SDL_Flip(display);
region_start_y = handle_character(
                                   up, UP, 
                                   0, /*This here, is my animation. */
                                  (region_start_x ), (region_start_y ), character, display);
aria.get_map(world, display);
if (chest_01_front == false)
{
    apply_surface(9*square_size, 10*square_size, items, display);
}
SDL_Flip(display);
region_start_y = handle_character(
                                   up, UP, 
                                   2, /*This here, is my animation. */
                                  (region_start_x ), (region_start_y ), character, display);
aria.get_map(world, display);
if (chest_01_front == false)
{
    apply_surface(9*square_size, 10*square_size, items, display);
}
SDL_Flip(display);
region_start_y = handle_character(
                                   up, UP, 
                                   3, /*This here, is my animation. */
                                  (region_start_x ), (region_start_y ), character, display);
[/PHP]

Now currently I repeat that code for how many animations I want (using c&p) I will be converting it to a while loop later though. >.<'

My problem is is that the images display a few microseconds too quickly. Any tips?

---

