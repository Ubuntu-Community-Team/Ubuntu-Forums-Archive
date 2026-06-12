---
title: "pyGame, rotate image in mouse direction?"
date: 2011-08-12
forum: Programming Talk
---

### Post by KoolPenguin on 2011-08-12
I'm trying to get my mouse image to rotate and point in the direction the mouse is moving.  For example, I have a space craft image that moves with the mouse and would like to rotate it to the correct angle and point in that direction.  The code below is what I have and the image does rotate when the mouse moves but not correctly.

```

def game(screen_resolution = (800, 600), fullscreen = False):
    pygame.init()
    
    if fullscreen:
        screen = pygame.display.set_mode((screen_resolution[0],screen_resolution[1]), pygame.FULLSCREEN)
    else:
        screen = pygame.display.set_mode((screen_resolution[0],screen_resolution[1]))
        
    background = pygame.Surface(screen.get_size())
    background.fill((255,255,255))
    background = background.convert()
    
    mouse_image = pygame.image.load(mif).convert_alpha()
    pygame.mouse.set_visible(False)
    
    clock = pygame.time.Clock()
    FPS = 30
    game_playtime = 0.0
    playgame = True
    
    while playgame is True:
        milliseconds = clock.tick(FPS)
        game_playtime += milliseconds / 1000.0
                
        x, y = pygame.mouse.get_pos()
        
        angle = atan2((y-300), (x-400))
        mouse_cursor = pygame.transform.rotate(mouse_image, degrees(angle))
        
        x -= mouse_cursor.get_width()/2
        y -= mouse_cursor.get_height()/2
        
        screen.blit(background, (0, 0))
        screen.blit(mouse_cursor, (x, y))
        
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                playgame = False
            elif event.type == pygame.KEYDOWN:
                if event.key == pygame.K_ESCAPE:
                    playgame = False

        pygame.display.set_caption('Press ESC to quit. FPS: %.2f (%ix%i), time: %.2f seonds' % (clock.get_fps(),
                                                                                                screen_resolution[0],
                                                                                                screen_resolution[1], game_playtime))
        pygame.display.flip()
        
    pygame.mouse.set_visible(True)


```

Thanks for any help that can be provided.

--
Chris

---

### Post by KoolPenguin on 2011-08-13
Made some changes to the angle calculations, works better but still not correct.  Here is the updated code and a video showing how it currently works. The image still doesn't point 100% in the direction of the mouse and does not rotate quick enough with the mouse motion.

Still would appreciate any help.

```

# mouse image file
mif = os.path.join('images', 'space_craft.png')


def game(screen_resolution = (800, 600), fullscreen = False):
    # initialize pygame system
    pygame.init()

    # set to fullscreen or window size
    if fullscreen:
        screen = pygame.display.set_mode((screen_resolution[0],screen_resolution[1]), pygame.FULLSCREEN)
    else:
        screen = pygame.display.set_mode((screen_resolution[0],screen_resolution[1]))

    # set background screen
    background = pygame.Surface(screen.get_size())
    background.fill((255,255,255))
    background = background.convert()

    # load mouse image and rotate 90 degrees
    mouse_image = pygame.image.load(mif).convert_alpha()
    mouse_image = pygame.transform.rotate(mouse_image, 90)

    # hide mouse cursor
    pygame.mouse.set_visible(False)

    clock = pygame.time.Clock()
    FPS = 30
    game_playtime = 0.0
    playgame = True

    # play game while true
    while playgame is True:
        
        milliseconds = clock.tick(FPS)
        
        # game time played in seconds
        game_playtime += milliseconds / 1000.0

        # get current mouse position
        x, y = pygame.mouse.get_pos()

        # get center of screen
        res_x = screen_resolution[0] / 2
        res_y = screen_resolution[1] / 2

        # get rotation angle of mouse location relative to center of screen
        angle = atan2((res_y - y), (x - res_x)) / pi * 2.0
        mouse_cursor = pygame.transform.rotate(mouse_image, degrees(angle))

        # set mouse cursor center of mouse image
        x -= mouse_cursor.get_width() / 2
        y -= mouse_cursor.get_height() / 2

        # put background and mouse cursor image to screen
        screen.blit(background, (0, 0))
        screen.blit(mouse_cursor, (x, y))

        # user inputs
        for event in pygame.event.get():
            
            if event.type == pygame.QUIT:
                playgame = False
            elif event.type == pygame.KEYDOWN:
                if event.key == pygame.K_ESCAPE:
                    playgame = False

        # update window caption
        pygame.display.set_caption('Press ESC to quit. FPS: %.2f (%ix%i), time: %.2f seonds' % (clock.get_fps(),
                                                                                                screen_resolution[0],
                                                                                                screen_resolution[1], game_playtime))
        # update the screen
        pygame.display.flip()

    # show mouse cursor
    pygame.mouse.set_visible(True)


```

Video showing how it current works:

[http://www.youtube.com/watch?v=0KJ7Z1RGo4k]("http://www.youtube.com/watch?v=0KJ7Z1RGo4k")

Thanks
--
Chris

---

### Post by sed0i97.1nc on 2011-09-29
&#1054;&#1075;&#1088;&#1086;&#1084;&#1085;&#1086;&#1077; &#1089;&#1087;&#1072;&#1089;&#1080;&#1073;&#1086;!
&#1044;&#1091;&#1084;&#1072;&#1102; &#1083;&#1091;&#1095;&#1096;&#1077; &#1089;&#1076;&#1077;&#1083;&#1072;&#1090;&#1100; &#1090;&#1072;&#1082;:
```

if x > mouse_x:
    self.d = math.atan2((mouse_y - y), (x - base.mouse_x)) / math.pi * 2.0
            
if x < mouse_x:
    self.d = math.atan2((mouse_y - y), (x - base.mouse_x)) / math.pi * 3.0

```

---

