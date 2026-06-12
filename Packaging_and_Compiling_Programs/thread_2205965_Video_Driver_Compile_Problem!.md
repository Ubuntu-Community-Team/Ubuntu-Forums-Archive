---
title: "Video Driver Compile Problem!"
date: 2014-02-16
forum: Packaging and Compiling Programs
---

### Post by neo6 on 2014-02-16
Hello World!

I am attempting to compile & install a video driver for my mythbuntu frontend box. Unfortunately it includes an onboard GPU that is not too popular. 

The drivers are for a S3 Chrome 450 ULP graphics card. And I am using mythbuntu 12.04.3

Here is my process, do not assume I know what I am doing.

First, when I ran the "make" command I received:

```
error: linux/smp_lock.h: No such file or directory
```

So therefore, I changed all instances of "linux/smp_lock.h" to "linux/smp.h"

This made the error go away when attempting to compile, but it presented me with a new error:

```
error: 'VM_RESERVED' undeclared (first use of this function)
```

Then, I changed "VM_RESERVED" to "[COLOR=#444444][FONT=arial]([/FONT][/COLOR][COLOR=#444444][FONT=arial]VM_DONTEXPAND [/FONT][/COLOR]| VM_DONTDUMP" and this fixed the above error. 

Now, I am receiving a new error to which I am currently stuck at and need the help of someone who is smarter at compiling than me. 

```
error: implicit declaration of function  'lock_kernel' [-Werror=implicit-function-declaration]
```

Here is the source file in reference to the above error: 

```

#include "s3gkeapi.h"
#define S3G_COMMAND_BASE S3G_IOCTL_NR(S3G_IOCTL_COMMAND_BASE)


static int s3g_setup(s3g_device_t* dev)
{
    atomic_set(&dev->ioctl_count, 0);
    
    dev->ctxlist = s3g_calloc(sizeof(*dev->ctxlist));


    if(dev->ctxlist == NULL)
    {
        return -ENOMEM;
    }


    INIT_LIST_HEAD(&dev->ctxlist->head);


    dev->sigdata.lock =
    dev->lock.hw_lock = s3g_calloc(sizeof(s3g_hw_lock_t));


    init_waitqueue_head(&dev->lock.lock_queue);
    return 0;
}




int s3g_open(struct inode* inode, struct file* filp)
{
    s3g_device_t* dev = NULL;
    s3g_file_t* priv;
#ifndef KERNEL_2_4
    int minor = iminor(inode);
#else
    int minor = MINOR(inode->i_rdev);
#endif
    int err = -ENODEV;


    if(!((minor >= 0) && (minor < cards_limit)))
    {
        return err;
    }


    if(!s3g_cards[minor])
    {
        return err;
    }


    if(!(dev = s3g_cards[minor]->dev))
    {
        return -err;
    }


    priv = s3g_calloc(sizeof(*priv));
    if(!priv)
    {
        return -ENOMEM;
    }


    // intilialize file private data
    filp->private_data = priv;


    priv->uid   = s3g_get_euid();
    priv->pid   = __s3gke_getpid();
    priv->minor = minor;
    priv->head  = s3g_cards[minor];
    priv->ioctl_count = 0;
    priv->lock_count  = 0;
    priv->filp        = filp;


    down(&dev->struct_sem);
    if(!dev->file_last)
    {
        priv->next = NULL;
        priv->prev = NULL;
        dev->file_first = priv;
        dev->file_last = priv;
    }
    else
    {
        priv->next = NULL;
        priv->prev = dev->file_last;
        dev->file_last->next = priv;
        dev->file_last = priv;
    }


    up(&dev->struct_sem);


    spin_lock(&dev->count_lock);
    if(!dev->open_count++)
    {
        spin_unlock(&dev->count_lock);
        return s3g_setup(dev);
    }
    spin_unlock(&dev->count_lock);


    return 0;
}




int s3g_release(struct inode* inode, struct file* filp)
{
    s3g_file_t* priv = filp->private_data;
    s3g_device_t* dev;


    lock_kernel();
    dev = priv->head->dev;


    if(priv->lock_count && dev->lock.hw_lock && S3G_LOCK_IS_HELD(dev->lock.hw_lock->lock) && dev->lock.filp == filp)
    {
        s3g_lock_free(dev, &dev->lock.hw_lock->lock, S3G_LOCKING_CONTEXT(dev->lock.hw_lock->lock));
    }


    down(&dev->ctxlist_sem);


    if(dev->ctxlist && (!list_empty(&dev->ctxlist->head)))
    {
        s3g_ctx_list_t* pos, *n;


        list_for_each_entry_safe(pos, n, &dev->ctxlist->head, head)
        {
            if(pos->tag == priv && pos->handle != S3G_KERNEL_CONTEXT)
            {
                s3g_ctxbitmap_free(dev, pos->handle);


                list_del(&pos->head);
                s3g_free(pos);
                --dev->ctx_count;
            }
        }
    }
    up(&dev->ctxlist_sem);


    down(&dev->struct_sem);


    if(priv->prev)
    {
        priv->prev->next = priv->next;
    }
    else
    {
        dev->file_first = priv->next;
    }


    if(priv->next)
    {
        priv->next->prev = priv->prev;
    }
    else
    {
        dev->file_last = priv->prev;
    }


    up(&dev->struct_sem);


    s3g_driver_cleanup(filp);


    s3g_free(priv);
    spin_lock(&dev->count_lock);
    if(!--dev->open_count)
    {
        if(atomic_read(&dev->ioctl_count)) //|| dev->blocked)
        {
            spin_unlock(&dev->count_lock);
            unlock_kernel();
            return -EBUSY;
        }


        spin_unlock(&dev->count_lock);
        unlock_kernel();
        return s3g_lastclose(dev);
    }


    spin_unlock(&dev->count_lock);


    unlock_kernel();


    return 0;
}




unsigned int s3g_poll(struct file *filp, struct poll_table_struct *wait)
{
    return 0;
}


int s3g_fasync(int fd, struct file* filp, int on)
{
    return 0;
}


int s3g_get_busid(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t* priv = filp->private_data;
    s3g_device_t* dev = priv->head->dev;
    s3g_unique_t __user* argp = (void __user*)arg;
    s3g_unique_t u;


    s3g_debug("Enter get bus id ioctl\n");


    if(copy_from_user(&u, argp, sizeof(u)))
    {
        return -EFAULT;
    }


    if(u.unique_len >= dev->unique_len)
    {
        if(copy_to_user(u.unique, dev->unique, dev->unique_len))
        {
            return -EFAULT;
        }
    }


    u.unique_len = dev->unique_len;


    if(copy_to_user(argp, &u, sizeof(u)))
    {
        return -EFAULT;
    }


    return 0;
}


int s3g_ioctl_get_display_info(struct inode* inode, struct file* filp, 
    unsigned int cmd, unsigned long arg)
{
    s3g_file_t*         priv = filp->private_data;
    s3g_device_t*       dev = priv->head->dev;
    s3g_display_info_t  display_info;  
    s3g_framebuffer*    fb;     
    int                 server_index = 0;
    int                 screen_index = 0;
    void __user*        argp = (void __user*)arg;
    int  i;
    int  retval  = 0;
    int  found = 0;
    down(&dev->struct_sem);


    if (copy_from_user(&display_info, argp, sizeof(s3g_display_info_t)))
    {
        up(&dev->struct_sem);
        return -EFAULT;
    }


    server_index = display_info.server_index;
    screen_index = display_info.screen_index;


    fb = (s3g_framebuffer*)s3g_get_fb(dev->hAdapter, server_index, screen_index);


    if(fb == NULL)
    {
        retval = -EINVAL;
        goto out;
    }


    display_info.bXinerama = s3g_servers[server_index].bXinerama;
    display_info.bufBpp = fb->bits_per_pixel/8;
    display_info.bUseRxa = fb->use_rxa;        
    display_info.bDuoView = fb->duoView;
    
    for(i = 0; i < MAX_IGAS; i++)
    {
        fb = s3g_get_fb_per_iga(dev->hAdapter, i);


        if(fb && fb->server_index == server_index)
        {
            display_info.iga2scrnIndex[i] = fb->scrnIndex;
        }
        else
        {
            display_info.iga2scrnIndex[i] = -1;
        }
    }
    
    if (copy_to_user(argp, &display_info, sizeof(display_info)))
    {
        retval = -EINVAL;
        goto out;
    }


out:
    up(&dev->struct_sem);    
    return retval;
}




int s3g_ioctl_get_iga_info(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t*    priv = filp->private_data;
    s3g_device_t*  dev  = priv->head->dev;
    s3g_iga_info_t   iga_info;


    void __user*   argp = (void __user*)arg;
 
    down(&dev->struct_sem);
  
    if(copy_from_user(&iga_info, argp, sizeof(s3g_iga_info_t)))
    {
        up(&dev->struct_sem);
        return -EFAULT;
    }


    s3g_get_iga_info(dev->hAdapter, &iga_info);
    
    up(&dev->struct_sem);
    
    copy_to_user(argp, &iga_info, sizeof(s3g_iga_info_t));
    
    return 0;
}
int s3g_ioctl_clip_notify(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_clipnotify_t __user* argp = (void __user*)arg;
    s3g_clipnotify_t clip;
    s3g_framebuffer *fb;    
    s3g_file_t*    priv = filp->private_data;
    s3g_device_t*  dev  = priv->head->dev;
    int i;


    if(copy_from_user(&clip, argp, sizeof(clip)))
    {
        return -EFAULT;
    }


    if(clip.scrnIndex > 4)
    {
        return -EFAULT;
    }


    down(&s3g_draw_sem);


    if(clip.kdrawId != 0)
    {
        i = clip.kdrawId;


        s3g_drawables[i].clipNotify[clip.scrnIndex].x = clip.x;
        s3g_drawables[i].clipNotify[clip.scrnIndex].y = clip.y;
        s3g_drawables[i].clipNotify[clip.scrnIndex].width = clip.width;
        s3g_drawables[i].clipNotify[clip.scrnIndex].height = clip.height;
        s3g_drawables[i].clipNotify[clip.scrnIndex].numClipRects = clip.numClipRects;
  
        if(clip.hAllocation)
        {
            s3g_drawables[i].hAllocation = clip.hAllocation;
        }
        else
        {
            fb = s3g_get_fb(dev->hAdapter, s3g_drawables[i].server_index, clip.scrnIndex);
            s3g_drawables[i].hAllocation = fb->hAllocation;
        }


        if(clip.numClipRects)
        {
            if(s3g_drawables[i].clipNotify[clip.scrnIndex].clipRects == 0)
            {
                s3g_drawables[i].clipNotify[clip.scrnIndex].clipRects = s3g_malloc(sizeof(s3g_clip_rect_t)*64);
            }


            memcpy(s3g_drawables[i].clipNotify[clip.scrnIndex].clipRects, clip.clipRects, sizeof(s3g_clip_rect_t)*clip.numClipRects);
        }


    }


    up(&s3g_draw_sem);




    return 0;
}


// Add kernel drawable
// And return a kernel drawable id to user mode
// Note the id is start from 1
// Clip list management use index 0
int s3g_ioctl_adddraw(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t*   priv = filp->private_data;
    s3g_device_t* dev  = priv->head->dev;
    
    unsigned int __user* argp = (void __user*)arg;
    unsigned int xId;
    int i;
    unsigned int drawId = 0;


    int found = 0;


    int server_index;


    s3g_drawable_t drawable;


    if(copy_from_user(&drawable, argp, sizeof(s3g_drawable_t)))
    {
        return -EFAULT;
    }


    xId = drawable.xId;
    server_index = drawable.server_index;


    down(&s3g_draw_sem);


    for(i = 1; i < S3G_MAX_DRAWABLES; i++)
    {
        if(s3g_drawables[i].xId == xId && s3g_drawables[i].server_index)
        {
            s3g_drawables[i].refCount++;
            found = 1;
            drawId = i;
            break;
        }
    }


    if(!found)
    {
        for(i = 1; i < S3G_MAX_DRAWABLES; i++)
        {
            if(s3g_drawables[i].xId == 0)
            {
                s3g_drawables[i].server_index = server_index;
                s3g_drawables[i].xId = xId;
                s3g_drawables[i].refCount++;
                found = 1;
                drawId = i;
                break;
            }
        }
    }


    if(server_index == 0)
    {
        // Nox driver has no clip notify mechanism, so set fb size as drawable size
        s3g_framebuffer* fb = (s3g_framebuffer*)s3g_get_fb(dev->hAdapter, 0, 0);
        i = drawId;


        s3g_drawables[i].clipNotify[0].x =0;
        s3g_drawables[i].clipNotify[0].y = 0;
        s3g_drawables[i].clipNotify[0].width = fb->width;
        s3g_drawables[i].clipNotify[0].height = fb->height;
        s3g_drawables[i].clipNotify[0].numClipRects = 1;


        if(s3g_drawables[i].clipNotify[0].clipRects == 0)
        {
            s3g_drawables[i].clipNotify[0].clipRects = s3g_malloc(sizeof(s3g_clip_rect_t)*1);
        }


        s3g_drawables[i].clipNotify[0].clipRects[0].x1 = 0;
        s3g_drawables[i].clipNotify[0].clipRects[0].y1 = 0;
        s3g_drawables[i].clipNotify[0].clipRects[0].x2 = fb->width;
        s3g_drawables[i].clipNotify[0].clipRects[0].y2 = fb->height;
        s3g_drawables[i].hAllocation = fb->hAllocation;
    }


    up(&s3g_draw_sem);


    if(found)
    {
        drawable.xId = drawId;
        if(copy_to_user(argp, &drawable, sizeof(drawable)))
        {
            return -EFAULT;
        }
    }
    else
    {
        return -EFAULT;
    }
    
    return 0;
    
}


int s3g_ioctl_rmdraw(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    unsigned int __user* argp = (void __user*)arg;
    unsigned int drawId = *argp;


    int i;


    if(drawId >= S3G_MAX_DRAWABLES)
    {
        return -EFAULT;
    }
 
    down(&s3g_draw_sem);


    if(!(--s3g_drawables[drawId].refCount))
    {
        for(i = 0; i < 4; i++)
        {
            if(s3g_drawables[drawId].clipNotify[i].clipRects)
            {
                s3g_free(s3g_drawables[drawId].clipNotify[i].clipRects);
            }
        }
        memset(&s3g_drawables[drawId], 0, sizeof(s3g_drawable_t));
    }


    up(&s3g_draw_sem);


    return 0;    


}


int s3g_ioctl_get_drawsize(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t*            priv = filp->private_data;
    s3g_device_t*       dev = priv->head->dev;
    
    s3g_get_drawsize_t __user* argp = (void __user*)arg;


    s3g_framebuffer* fb;
    int server_index;
    unsigned int drawId = argp->drawId;
    s3g_get_drawsize_t drawRec;
    int i;


    if(drawId > S3G_MAX_DRAWABLES)
    {
        return -EFAULT;
    }


    memset(&drawRec, 0, sizeof(drawRec));


    down(&s3g_draw_sem);


    // For samm case
    // Xinerama: drawable size is the same for all screen, so any screen is ok.
    // Individual displays: the clip list and drawable size is just stored acording to the scrnIndex
    // And there is just one entry, so need to search to get it.
    for(i = 0; i < 4; i++)
    {
        if(s3g_drawables[drawId].clipNotify[i].width != 0)
        {
            drawRec.drawId       = drawId;
            drawRec.rect.x1      = s3g_drawables[drawId].clipNotify[i].x;
            drawRec.rect.y1      = s3g_drawables[drawId].clipNotify[i].y;
            drawRec.rect.x2      = s3g_drawables[drawId].clipNotify[i].width + drawRec.rect.x1;
            drawRec.rect.y2      = s3g_drawables[drawId].clipNotify[i].height + drawRec.rect.y1;
            break;
        }
    }
    if (i >= 4)
    {
        up(&s3g_draw_sem);
        return -EFAULT;  
    }
    server_index = s3g_drawables[drawId].server_index;
    drawRec.server_index = server_index;
    drawRec.scrnIndex = i;
    drawRec.fullscreen = s3g_drawable_fullscreen(dev->hAdapter, &drawRec);
    /* if rotation is available, fullscreen mode is not supported */
    fb = (s3g_framebuffer*)s3g_get_fb(dev->hAdapter, server_index, i);
    drawRec.fullscreen &= !(fb->rotate);
    drawRec.redirect = (fb->hAllocation != s3g_drawables[drawId].hAllocation);
    up(&s3g_draw_sem);


    if(copy_to_user(argp, &drawRec, sizeof(drawRec)))
    {
        return -EFAULT;
    }


    return 0;
    
}


int s3g_ioctl_get_mode_config(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t* priv = filp->private_data;
    s3g_device_t* dev = priv->head->dev;


    void __user* argp = (void __user*)arg;


    s3g_get_mode_config(dev->hAdapter, argp);
 
    return 0;
}


int s3g_ioctl_get_connector(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t* priv = filp->private_data;
    s3g_device_t* dev = priv->head->dev;


    void __user* argp = (void __user*)arg;


    s3g_get_connector(dev->hAdapter, argp);
  
    return 0;
}


int s3g_ioctl_mode_set(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t* priv = filp->private_data;
    s3g_device_t* dev = priv->head->dev;


    void __user* argp = (void __user*)arg;
    s3g_modeset_t mode_set;


    if(copy_from_user(&mode_set, argp, sizeof(s3g_modeset_t)))
    {
        return -EFAULT;
    }


    mode_set.fb = s3g_get_fb(dev->hAdapter, mode_set.server_index, mode_set.fb_id);


    s3g_mode_set(dev->hAdapter, &mode_set);
 
    return 0;
}


int s3g_ioctl_cursor(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t* priv = filp->private_data;
    s3g_device_t* dev = priv->head->dev;


    void __user* argp = (void __user*)arg;


    s3g_cursorset_t cursor_set;


     if(copy_from_user(&cursor_set, argp, sizeof(s3g_cursorset_t)))
    {
        return -EFAULT;
    }


     s3g_set_cursor(dev->hAdapter, &cursor_set);


 
    return 0;
}


int s3g_ioctl_gamma(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t*   priv = filp->private_data;
    s3g_device_t* dev  = priv->head->dev;
    void __user*  argp = (void __user*)arg;
    int           ret  = -EFAULT;


    s3g_gamma_set_t gamma_set;


    char* red   = s3g_malloc(256 + 256 + 256);
    char* green = red + 256;
    char* blue  = red + 256 + 256;


    if(!copy_from_user(&gamma_set, argp, sizeof(gamma_set)) 
       && !copy_from_user(red, gamma_set.red, 256) 
       && !copy_from_user(green, gamma_set.green, 256) 
       && !copy_from_user(blue, gamma_set.blue, 256))
    {
        gamma_set.red = red;
        gamma_set.green = green;
        gamma_set.blue = blue;
    
        s3g_set_gamma(dev->hAdapter, &gamma_set);


        ret = 0;
    }


    s3g_free(red);


    return ret;
}


int s3g_ioctl_dpms(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t* priv = filp->private_data;
    s3g_device_t* dev = priv->head->dev;


    void __user* argp = (void __user*)arg;


    s3g_dpms_set_t dpms_set;
    
    if(copy_from_user(&dpms_set, argp, sizeof(dpms_set)))
    {
        return -EFAULT;
    }


    s3g_set_dpms(dev->hAdapter, &dpms_set);


    return 0;
    
}


int s3g_ioctl_get_mode_timing(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t* priv = filp->private_data;
    s3g_device_t* dev = priv->head->dev;


    void __user* argp = (void __user*)arg;


    s3g_mode_timing_info_t timing_info;


    if(copy_from_user(&timing_info, argp, sizeof(timing_info)))
    {
        return -EFAULT;
    }


    if (s3g_get_mode_timing(dev->hAdapter, &timing_info))
    {
        return -EFAULT;
    }  


    if(copy_to_user(argp, &timing_info, sizeof(timing_info)))
    {
        return -EFAULT;
    }
    return 0;
}




int s3g_ioctl_leave_vt(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t* priv = filp->private_data;
    s3g_device_t* dev = priv->head->dev;    
    
    /*if have fb driver, just return*/
    if(!dev->nofb)
    {
        return 0;
    }


    s3g_leave_vt(dev->hAdapter);


    return 0;
}


int s3g_ioctl_check_device_combination(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t* priv = filp->private_data;
    s3g_device_t* dev = priv->head->dev;


    void __user* argp = (void __user*)arg;


    s3g_check_device_combination_t device_combination;


    if(copy_from_user(&device_combination, argp, sizeof(device_combination)))
    {
        return -EFAULT;
    }


    if (s3g_check_device_combination(dev->hAdapter, &device_combination))
    {
        return -EFAULT;
    }  
    
    if(copy_to_user(argp, &device_combination, sizeof(device_combination)))
    {
        return -EFAULT;
    }


    return 0;
}


s3g_ioctl_t s3g_common_ioctls[] =
{
    [S3G_IOCTL_NR(S3G_IOCTL_GET_BUSID)] = s3g_get_busid,
    [S3G_IOCTL_NR(S3G_IOCTL_GET_DISPLAYINFO)] = s3g_ioctl_get_display_info,
    [S3G_IOCTL_NR(S3G_IOCTL_GET_IGAINFO)] = s3g_ioctl_get_iga_info,
    [S3G_IOCTL_NR(S3G_IOCTL_ADD_CTX)] = s3g_addctx,
    [S3G_IOCTL_NR(S3G_IOCTL_RM_CTX)] = s3g_rmctx,
    [S3G_IOCTL_NR(S3G_IOCTL_LOCK)] = s3g_lock,
    [S3G_IOCTL_NR(S3G_IOCTL_UNLOCK)] = s3g_unlock,
    [S3G_IOCTL_NR(S3G_IOCTL_CLIP_NOTIFY)] = s3g_ioctl_clip_notify,
    [S3G_IOCTL_NR(S3G_IOCTL_ADD_DRAW)] = s3g_ioctl_adddraw,
    [S3G_IOCTL_NR(S3G_IOCTL_RM_DRAW)] = s3g_ioctl_rmdraw,
    [S3G_IOCTL_NR(S3G_IOCTL_GET_DRAWSIZE)] = s3g_ioctl_get_drawsize,
    [S3G_IOCTL_NR(S3G_IOCTL_GET_MODE_CONFIG)] = s3g_ioctl_get_mode_config,
    [S3G_IOCTL_NR(S3G_IOCTL_GET_OUTPUT)] = s3g_ioctl_get_connector,
    [S3G_IOCTL_NR(S3G_IOCTL_MODE_SET)] = s3g_ioctl_mode_set,
    [S3G_IOCTL_NR(S3G_IOCTL_CURSOR)] = s3g_ioctl_cursor,
    [S3G_IOCTL_NR(S3G_IOCTL_GAMMA)] = s3g_ioctl_gamma,
    [S3G_IOCTL_NR(S3G_IOCTL_DPMS)] = s3g_ioctl_dpms,
    [S3G_IOCTL_NR(S3G_IOCTL_GET_MODE_TIMING)] = s3g_ioctl_get_mode_timing,
    [S3G_IOCTL_NR(S3G_IOCTL_LEAVE_VT)] = s3g_ioctl_leave_vt, 
    [S3G_IOCTL_NR(S3G_IOCTL_CHECK_DEVICE_COMBINATION)] = s3g_ioctl_check_device_combination, 
};


extern s3g_ioctl_t s3g_ioctls[];


int s3g_ioctl(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t* priv = filp->private_data;
    s3g_device_t* dev = priv->head->dev;
    s3g_ioctl_t func = NULL;
    unsigned int nr = S3G_IOCTL_NR(cmd);


    int ret = -EINVAL;


    atomic_inc(&dev->ioctl_count);
    ++priv->ioctl_count;


    if(nr < sizeof(s3g_common_ioctls)/sizeof(s3g_ioctl_t))
    {
        func = s3g_common_ioctls[nr];
    }
    else if(nr >= S3G_COMMAND_BASE)
    {
        func = s3g_ioctls[nr - S3G_COMMAND_BASE];
    }
    
    ret = func(inode, filp, cmd, arg);


    return ret;
}




#if defined(__x86_64__) && defined(HAVE_COMPAT_IOCTL)
long s3g_compat_ioctl(struct file* filp, unsigned int cmd, unsigned long arg)
{
    return s3g_ioctl(filp->f_dentry->d_inode, filp, cmd, arg);
}
#endif

```

Any and all help will be appreciated!

---

### Post by neo6 on 2014-02-16
Hello World!

I am attempting to compile a video card driver for my kernel and I receive the following errors. I would greatly appreciate any and all help as this isn't my forte.

Before asked, I do have the latest build-essentials installed.

Errors received when compiling:

```

s3g_fops.c:103:5: error: implicit declaration of function \u2018lock_kernel\u2019 [-Werror=implicit-function-declaration]
s3g_fops.c:162:13: error: implicit declaration of function \u2018unlock_kernel\u2019 [-Werror=implicit-function-declaration]
s3g_fops.c: In function \u2018s3g_get_busid\u2019:
s3g_fops.c:196:14: warning: statement with no effect [-Wunused-value]
s3g_fops.c: In function \u2018s3g_ioctl_get_display_info\u2019:
s3g_fops.c:233:10: warning: unused variable \u2018found\u2019 [-Wunused-variable]
cc1: some warnings being treated as errors
s3g_fops.o] Error 1

```




Source file:

```

#include "s3gkeapi.h"
#define S3G_COMMAND_BASE S3G_IOCTL_NR(S3G_IOCTL_COMMAND_BASE)


static int s3g_setup(s3g_device_t* dev)
{
    atomic_set(&dev->ioctl_count, 0);
    
    dev->ctxlist = s3g_calloc(sizeof(*dev->ctxlist));


    if(dev->ctxlist == NULL)
    {
        return -ENOMEM;
    }


    INIT_LIST_HEAD(&dev->ctxlist->head);


    dev->sigdata.lock =
    dev->lock.hw_lock = s3g_calloc(sizeof(s3g_hw_lock_t));


    init_waitqueue_head(&dev->lock.lock_queue);
    return 0;
}




int s3g_open(struct inode* inode, struct file* filp)
{
    s3g_device_t* dev = NULL;
    s3g_file_t* priv;
#ifndef KERNEL_2_4
    int minor = iminor(inode);
#else
    int minor = MINOR(inode->i_rdev);
#endif
    int err = -ENODEV;


    if(!((minor >= 0) && (minor < cards_limit)))
    {
        return err;
    }


    if(!s3g_cards[minor])
    {
        return err;
    }


    if(!(dev = s3g_cards[minor]->dev))
    {
        return -err;
    }


    priv = s3g_calloc(sizeof(*priv));
    if(!priv)
    {
        return -ENOMEM;
    }


    // intilialize file private data
    filp->private_data = priv;


    priv->uid   = s3g_get_euid();
    priv->pid   = __s3gke_getpid();
    priv->minor = minor;
    priv->head  = s3g_cards[minor];
    priv->ioctl_count = 0;
    priv->lock_count  = 0;
    priv->filp        = filp;


    down(&dev->struct_sem);
    if(!dev->file_last)
    {
        priv->next = NULL;
        priv->prev = NULL;
        dev->file_first = priv;
        dev->file_last = priv;
    }
    else
    {
        priv->next = NULL;
        priv->prev = dev->file_last;
        dev->file_last->next = priv;
        dev->file_last = priv;
    }


    up(&dev->struct_sem);


    spin_lock(&dev->count_lock);
    if(!dev->open_count++)
    {
        spin_unlock(&dev->count_lock);
        return s3g_setup(dev);
    }
    spin_unlock(&dev->count_lock);


    return 0;
}




int s3g_release(struct inode* inode, struct file* filp)
{
    s3g_file_t* priv = filp->private_data;
    s3g_device_t* dev;


    lock_kernel();
    dev = priv->head->dev;


    if(priv->lock_count && dev->lock.hw_lock && S3G_LOCK_IS_HELD(dev->lock.hw_lock->lock) && dev->lock.filp == filp)
    {
        s3g_lock_free(dev, &dev->lock.hw_lock->lock, S3G_LOCKING_CONTEXT(dev->lock.hw_lock->lock));
    }


    down(&dev->ctxlist_sem);


    if(dev->ctxlist && (!list_empty(&dev->ctxlist->head)))
    {
        s3g_ctx_list_t* pos, *n;


        list_for_each_entry_safe(pos, n, &dev->ctxlist->head, head)
        {
            if(pos->tag == priv && pos->handle != S3G_KERNEL_CONTEXT)
            {
                s3g_ctxbitmap_free(dev, pos->handle);


                list_del(&pos->head);
                s3g_free(pos);
                --dev->ctx_count;
            }
        }
    }
    up(&dev->ctxlist_sem);


    down(&dev->struct_sem);


    if(priv->prev)
    {
        priv->prev->next = priv->next;
    }
    else
    {
        dev->file_first = priv->next;
    }


    if(priv->next)
    {
        priv->next->prev = priv->prev;
    }
    else
    {
        dev->file_last = priv->prev;
    }


    up(&dev->struct_sem);


    s3g_driver_cleanup(filp);


    s3g_free(priv);
    spin_lock(&dev->count_lock);
    if(!--dev->open_count)
    {
        if(atomic_read(&dev->ioctl_count)) //|| dev->blocked)
        {
            spin_unlock(&dev->count_lock);
            unlock_kernel();
            return -EBUSY;
        }


        spin_unlock(&dev->count_lock);
        unlock_kernel();
        return s3g_lastclose(dev);
    }


    spin_unlock(&dev->count_lock);


    unlock_kernel();


    return 0;
}




unsigned int s3g_poll(struct file *filp, struct poll_table_struct *wait)
{
    return 0;
}


int s3g_fasync(int fd, struct file* filp, int on)
{
    return 0;
}


int s3g_get_busid(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t* priv = filp->private_data;
    s3g_device_t* dev = priv->head->dev;
    s3g_unique_t __user* argp = (void __user*)arg;
    s3g_unique_t u;


    s3g_debug("Enter get bus id ioctl\n");


    if(copy_from_user(&u, argp, sizeof(u)))
    {
        return -EFAULT;
    }


    if(u.unique_len >= dev->unique_len)
    {
        if(copy_to_user(u.unique, dev->unique, dev->unique_len))
        {
            return -EFAULT;
        }
    }


    u.unique_len = dev->unique_len;


    if(copy_to_user(argp, &u, sizeof(u)))
    {
        return -EFAULT;
    }


    return 0;
}


int s3g_ioctl_get_display_info(struct inode* inode, struct file* filp, 
    unsigned int cmd, unsigned long arg)
{
    s3g_file_t*         priv = filp->private_data;
    s3g_device_t*       dev = priv->head->dev;
    s3g_display_info_t  display_info;  
    s3g_framebuffer*    fb;     
    int                 server_index = 0;
    int                 screen_index = 0;
    void __user*        argp = (void __user*)arg;
    int  i;
    int  retval  = 0;
    int  found = 0;
    down(&dev->struct_sem);


    if (copy_from_user(&display_info, argp, sizeof(s3g_display_info_t)))
    {
        up(&dev->struct_sem);
        return -EFAULT;
    }


    server_index = display_info.server_index;
    screen_index = display_info.screen_index;


    fb = (s3g_framebuffer*)s3g_get_fb(dev->hAdapter, server_index, screen_index);


    if(fb == NULL)
    {
        retval = -EINVAL;
        goto out;
    }


    display_info.bXinerama = s3g_servers[server_index].bXinerama;
    display_info.bufBpp = fb->bits_per_pixel/8;
    display_info.bUseRxa = fb->use_rxa;        
    display_info.bDuoView = fb->duoView;
    
    for(i = 0; i < MAX_IGAS; i++)
    {
        fb = s3g_get_fb_per_iga(dev->hAdapter, i);


        if(fb && fb->server_index == server_index)
        {
            display_info.iga2scrnIndex[i] = fb->scrnIndex;
        }
        else
        {
            display_info.iga2scrnIndex[i] = -1;
        }
    }
    
    if (copy_to_user(argp, &display_info, sizeof(display_info)))
    {
        retval = -EINVAL;
        goto out;
    }


out:
    up(&dev->struct_sem);    
    return retval;
}




int s3g_ioctl_get_iga_info(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t*    priv = filp->private_data;
    s3g_device_t*  dev  = priv->head->dev;
    s3g_iga_info_t   iga_info;


    void __user*   argp = (void __user*)arg;
 
    down(&dev->struct_sem);
  
    if(copy_from_user(&iga_info, argp, sizeof(s3g_iga_info_t)))
    {
        up(&dev->struct_sem);
        return -EFAULT;
    }


    s3g_get_iga_info(dev->hAdapter, &iga_info);
    
    up(&dev->struct_sem);
    
    copy_to_user(argp, &iga_info, sizeof(s3g_iga_info_t));
    
    return 0;
}
int s3g_ioctl_clip_notify(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_clipnotify_t __user* argp = (void __user*)arg;
    s3g_clipnotify_t clip;
    s3g_framebuffer *fb;    
    s3g_file_t*    priv = filp->private_data;
    s3g_device_t*  dev  = priv->head->dev;
    int i;


    if(copy_from_user(&clip, argp, sizeof(clip)))
    {
        return -EFAULT;
    }


    if(clip.scrnIndex > 4)
    {
        return -EFAULT;
    }


    down(&s3g_draw_sem);


    if(clip.kdrawId != 0)
    {
        i = clip.kdrawId;


        s3g_drawables[i].clipNotify[clip.scrnIndex].x = clip.x;
        s3g_drawables[i].clipNotify[clip.scrnIndex].y = clip.y;
        s3g_drawables[i].clipNotify[clip.scrnIndex].width = clip.width;
        s3g_drawables[i].clipNotify[clip.scrnIndex].height = clip.height;
        s3g_drawables[i].clipNotify[clip.scrnIndex].numClipRects = clip.numClipRects;
  
        if(clip.hAllocation)
        {
            s3g_drawables[i].hAllocation = clip.hAllocation;
        }
        else
        {
            fb = s3g_get_fb(dev->hAdapter, s3g_drawables[i].server_index, clip.scrnIndex);
            s3g_drawables[i].hAllocation = fb->hAllocation;
        }


        if(clip.numClipRects)
        {
            if(s3g_drawables[i].clipNotify[clip.scrnIndex].clipRects == 0)
            {
                s3g_drawables[i].clipNotify[clip.scrnIndex].clipRects = s3g_malloc(sizeof(s3g_clip_rect_t)*64);
            }


            memcpy(s3g_drawables[i].clipNotify[clip.scrnIndex].clipRects, clip.clipRects, sizeof(s3g_clip_rect_t)*clip.numClipRects);
        }


    }


    up(&s3g_draw_sem);




    return 0;
}


// Add kernel drawable
// And return a kernel drawable id to user mode
// Note the id is start from 1
// Clip list management use index 0
int s3g_ioctl_adddraw(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t*   priv = filp->private_data;
    s3g_device_t* dev  = priv->head->dev;
    
    unsigned int __user* argp = (void __user*)arg;
    unsigned int xId;
    int i;
    unsigned int drawId = 0;


    int found = 0;


    int server_index;


    s3g_drawable_t drawable;


    if(copy_from_user(&drawable, argp, sizeof(s3g_drawable_t)))
    {
        return -EFAULT;
    }


    xId = drawable.xId;
    server_index = drawable.server_index;


    down(&s3g_draw_sem);


    for(i = 1; i < S3G_MAX_DRAWABLES; i++)
    {
        if(s3g_drawables[i].xId == xId && s3g_drawables[i].server_index)
        {
            s3g_drawables[i].refCount++;
            found = 1;
            drawId = i;
            break;
        }
    }


    if(!found)
    {
        for(i = 1; i < S3G_MAX_DRAWABLES; i++)
        {
            if(s3g_drawables[i].xId == 0)
            {
                s3g_drawables[i].server_index = server_index;
                s3g_drawables[i].xId = xId;
                s3g_drawables[i].refCount++;
                found = 1;
                drawId = i;
                break;
            }
        }
    }


    if(server_index == 0)
    {
        // Nox driver has no clip notify mechanism, so set fb size as drawable size
        s3g_framebuffer* fb = (s3g_framebuffer*)s3g_get_fb(dev->hAdapter, 0, 0);
        i = drawId;


        s3g_drawables[i].clipNotify[0].x =0;
        s3g_drawables[i].clipNotify[0].y = 0;
        s3g_drawables[i].clipNotify[0].width = fb->width;
        s3g_drawables[i].clipNotify[0].height = fb->height;
        s3g_drawables[i].clipNotify[0].numClipRects = 1;


        if(s3g_drawables[i].clipNotify[0].clipRects == 0)
        {
            s3g_drawables[i].clipNotify[0].clipRects = s3g_malloc(sizeof(s3g_clip_rect_t)*1);
        }


        s3g_drawables[i].clipNotify[0].clipRects[0].x1 = 0;
        s3g_drawables[i].clipNotify[0].clipRects[0].y1 = 0;
        s3g_drawables[i].clipNotify[0].clipRects[0].x2 = fb->width;
        s3g_drawables[i].clipNotify[0].clipRects[0].y2 = fb->height;
        s3g_drawables[i].hAllocation = fb->hAllocation;
    }


    up(&s3g_draw_sem);


    if(found)
    {
        drawable.xId = drawId;
        if(copy_to_user(argp, &drawable, sizeof(drawable)))
        {
            return -EFAULT;
        }
    }
    else
    {
        return -EFAULT;
    }
    
    return 0;
    
}


int s3g_ioctl_rmdraw(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    unsigned int __user* argp = (void __user*)arg;
    unsigned int drawId = *argp;


    int i;


    if(drawId >= S3G_MAX_DRAWABLES)
    {
        return -EFAULT;
    }
 
    down(&s3g_draw_sem);


    if(!(--s3g_drawables[drawId].refCount))
    {
        for(i = 0; i < 4; i++)
        {
            if(s3g_drawables[drawId].clipNotify[i].clipRects)
            {
                s3g_free(s3g_drawables[drawId].clipNotify[i].clipRects);
            }
        }
        memset(&s3g_drawables[drawId], 0, sizeof(s3g_drawable_t));
    }


    up(&s3g_draw_sem);


    return 0;    


}


int s3g_ioctl_get_drawsize(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t*            priv = filp->private_data;
    s3g_device_t*       dev = priv->head->dev;
    
    s3g_get_drawsize_t __user* argp = (void __user*)arg;


    s3g_framebuffer* fb;
    int server_index;
    unsigned int drawId = argp->drawId;
    s3g_get_drawsize_t drawRec;
    int i;


    if(drawId > S3G_MAX_DRAWABLES)
    {
        return -EFAULT;
    }


    memset(&drawRec, 0, sizeof(drawRec));


    down(&s3g_draw_sem);


    // For samm case
    // Xinerama: drawable size is the same for all screen, so any screen is ok.
    // Individual displays: the clip list and drawable size is just stored acording to the scrnIndex
    // And there is just one entry, so need to search to get it.
    for(i = 0; i < 4; i++)
    {
        if(s3g_drawables[drawId].clipNotify[i].width != 0)
        {
            drawRec.drawId       = drawId;
            drawRec.rect.x1      = s3g_drawables[drawId].clipNotify[i].x;
            drawRec.rect.y1      = s3g_drawables[drawId].clipNotify[i].y;
            drawRec.rect.x2      = s3g_drawables[drawId].clipNotify[i].width + drawRec.rect.x1;
            drawRec.rect.y2      = s3g_drawables[drawId].clipNotify[i].height + drawRec.rect.y1;
            break;
        }
    }
    if (i >= 4)
    {
        up(&s3g_draw_sem);
        return -EFAULT;  
    }
    server_index = s3g_drawables[drawId].server_index;
    drawRec.server_index = server_index;
    drawRec.scrnIndex = i;
    drawRec.fullscreen = s3g_drawable_fullscreen(dev->hAdapter, &drawRec);
    /* if rotation is available, fullscreen mode is not supported */
    fb = (s3g_framebuffer*)s3g_get_fb(dev->hAdapter, server_index, i);
    drawRec.fullscreen &= !(fb->rotate);
    drawRec.redirect = (fb->hAllocation != s3g_drawables[drawId].hAllocation);
    up(&s3g_draw_sem);


    if(copy_to_user(argp, &drawRec, sizeof(drawRec)))
    {
        return -EFAULT;
    }


    return 0;
    
}


int s3g_ioctl_get_mode_config(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t* priv = filp->private_data;
    s3g_device_t* dev = priv->head->dev;


    void __user* argp = (void __user*)arg;


    s3g_get_mode_config(dev->hAdapter, argp);
 
    return 0;
}


int s3g_ioctl_get_connector(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t* priv = filp->private_data;
    s3g_device_t* dev = priv->head->dev;


    void __user* argp = (void __user*)arg;


    s3g_get_connector(dev->hAdapter, argp);
  
    return 0;
}


int s3g_ioctl_mode_set(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t* priv = filp->private_data;
    s3g_device_t* dev = priv->head->dev;


    void __user* argp = (void __user*)arg;
    s3g_modeset_t mode_set;


    if(copy_from_user(&mode_set, argp, sizeof(s3g_modeset_t)))
    {
        return -EFAULT;
    }


    mode_set.fb = s3g_get_fb(dev->hAdapter, mode_set.server_index, mode_set.fb_id);


    s3g_mode_set(dev->hAdapter, &mode_set);
 
    return 0;
}


int s3g_ioctl_cursor(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t* priv = filp->private_data;
    s3g_device_t* dev = priv->head->dev;


    void __user* argp = (void __user*)arg;


    s3g_cursorset_t cursor_set;


     if(copy_from_user(&cursor_set, argp, sizeof(s3g_cursorset_t)))
    {
        return -EFAULT;
    }


     s3g_set_cursor(dev->hAdapter, &cursor_set);


 
    return 0;
}


int s3g_ioctl_gamma(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t*   priv = filp->private_data;
    s3g_device_t* dev  = priv->head->dev;
    void __user*  argp = (void __user*)arg;
    int           ret  = -EFAULT;


    s3g_gamma_set_t gamma_set;


    char* red   = s3g_malloc(256 + 256 + 256);
    char* green = red + 256;
    char* blue  = red + 256 + 256;


    if(!copy_from_user(&gamma_set, argp, sizeof(gamma_set)) 
       && !copy_from_user(red, gamma_set.red, 256) 
       && !copy_from_user(green, gamma_set.green, 256) 
       && !copy_from_user(blue, gamma_set.blue, 256))
    {
        gamma_set.red = red;
        gamma_set.green = green;
        gamma_set.blue = blue;
    
        s3g_set_gamma(dev->hAdapter, &gamma_set);


        ret = 0;
    }


    s3g_free(red);


    return ret;
}


int s3g_ioctl_dpms(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t* priv = filp->private_data;
    s3g_device_t* dev = priv->head->dev;


    void __user* argp = (void __user*)arg;


    s3g_dpms_set_t dpms_set;
    
    if(copy_from_user(&dpms_set, argp, sizeof(dpms_set)))
    {
        return -EFAULT;
    }


    s3g_set_dpms(dev->hAdapter, &dpms_set);


    return 0;
    
}


int s3g_ioctl_get_mode_timing(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t* priv = filp->private_data;
    s3g_device_t* dev = priv->head->dev;


    void __user* argp = (void __user*)arg;


    s3g_mode_timing_info_t timing_info;


    if(copy_from_user(&timing_info, argp, sizeof(timing_info)))
    {
        return -EFAULT;
    }


    if (s3g_get_mode_timing(dev->hAdapter, &timing_info))
    {
        return -EFAULT;
    }  


    if(copy_to_user(argp, &timing_info, sizeof(timing_info)))
    {
        return -EFAULT;
    }
    return 0;
}




int s3g_ioctl_leave_vt(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t* priv = filp->private_data;
    s3g_device_t* dev = priv->head->dev;    
    
    /*if have fb driver, just return*/
    if(!dev->nofb)
    {
        return 0;
    }


    s3g_leave_vt(dev->hAdapter);


    return 0;
}


int s3g_ioctl_check_device_combination(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t* priv = filp->private_data;
    s3g_device_t* dev = priv->head->dev;


    void __user* argp = (void __user*)arg;


    s3g_check_device_combination_t device_combination;


    if(copy_from_user(&device_combination, argp, sizeof(device_combination)))
    {
        return -EFAULT;
    }


    if (s3g_check_device_combination(dev->hAdapter, &device_combination))
    {
        return -EFAULT;
    }  
    
    if(copy_to_user(argp, &device_combination, sizeof(device_combination)))
    {
        return -EFAULT;
    }


    return 0;
}


s3g_ioctl_t s3g_common_ioctls[] =
{
    [S3G_IOCTL_NR(S3G_IOCTL_GET_BUSID)] = s3g_get_busid,
    [S3G_IOCTL_NR(S3G_IOCTL_GET_DISPLAYINFO)] = s3g_ioctl_get_display_info,
    [S3G_IOCTL_NR(S3G_IOCTL_GET_IGAINFO)] = s3g_ioctl_get_iga_info,
    [S3G_IOCTL_NR(S3G_IOCTL_ADD_CTX)] = s3g_addctx,
    [S3G_IOCTL_NR(S3G_IOCTL_RM_CTX)] = s3g_rmctx,
    [S3G_IOCTL_NR(S3G_IOCTL_LOCK)] = s3g_lock,
    [S3G_IOCTL_NR(S3G_IOCTL_UNLOCK)] = s3g_unlock,
    [S3G_IOCTL_NR(S3G_IOCTL_CLIP_NOTIFY)] = s3g_ioctl_clip_notify,
    [S3G_IOCTL_NR(S3G_IOCTL_ADD_DRAW)] = s3g_ioctl_adddraw,
    [S3G_IOCTL_NR(S3G_IOCTL_RM_DRAW)] = s3g_ioctl_rmdraw,
    [S3G_IOCTL_NR(S3G_IOCTL_GET_DRAWSIZE)] = s3g_ioctl_get_drawsize,
    [S3G_IOCTL_NR(S3G_IOCTL_GET_MODE_CONFIG)] = s3g_ioctl_get_mode_config,
    [S3G_IOCTL_NR(S3G_IOCTL_GET_OUTPUT)] = s3g_ioctl_get_connector,
    [S3G_IOCTL_NR(S3G_IOCTL_MODE_SET)] = s3g_ioctl_mode_set,
    [S3G_IOCTL_NR(S3G_IOCTL_CURSOR)] = s3g_ioctl_cursor,
    [S3G_IOCTL_NR(S3G_IOCTL_GAMMA)] = s3g_ioctl_gamma,
    [S3G_IOCTL_NR(S3G_IOCTL_DPMS)] = s3g_ioctl_dpms,
    [S3G_IOCTL_NR(S3G_IOCTL_GET_MODE_TIMING)] = s3g_ioctl_get_mode_timing,
    [S3G_IOCTL_NR(S3G_IOCTL_LEAVE_VT)] = s3g_ioctl_leave_vt, 
    [S3G_IOCTL_NR(S3G_IOCTL_CHECK_DEVICE_COMBINATION)] = s3g_ioctl_check_device_combination, 
};


extern s3g_ioctl_t s3g_ioctls[];


int s3g_ioctl(struct inode* inode, struct file* filp, unsigned int cmd, unsigned long arg)
{
    s3g_file_t* priv = filp->private_data;
    s3g_device_t* dev = priv->head->dev;
    s3g_ioctl_t func = NULL;
    unsigned int nr = S3G_IOCTL_NR(cmd);


    int ret = -EINVAL;


    atomic_inc(&dev->ioctl_count);
    ++priv->ioctl_count;


    if(nr < sizeof(s3g_common_ioctls)/sizeof(s3g_ioctl_t))
    {
        func = s3g_common_ioctls[nr];
    }
    else if(nr >= S3G_COMMAND_BASE)
    {
        func = s3g_ioctls[nr - S3G_COMMAND_BASE];
    }
    
    ret = func(inode, filp, cmd, arg);


    return ret;
}




#if defined(__x86_64__) && defined(HAVE_COMPAT_IOCTL)
long s3g_compat_ioctl(struct file* filp, unsigned int cmd, unsigned long arg)
{
    return s3g_ioctl(filp->f_dentry->d_inode, filp, cmd, arg);
}
#endif

```

---

### Post by bapoumba on 2014-02-17
Threads merged.

---

### Post by steeldriver on 2014-02-18
I don't have any experience with this problem, but I doubt that simply replacing a missing header with a different one is going to work (as far as I know, smp.h does not supersede smp_lock.h and doesn't contain the required declarations)

The more fundamental issue is that the driver you're trying to compile is out of date, and smp_lock has been removed from the kernel source since 2.6.something. The best solution would be to find a newer driver, however I realize that may not be an option since the S3 devices are not well supported. If you absolutely can't find an alternative, then there *may* be a way to modify the source to use mutexes - see here [http://stackoverflow.com/questions/5956145/can-someone-help-me-replace-lock-kernel-on-a-block-device-driver](http://stackoverflow.com/questions/5956145/can-someone-help-me-replace-lock-kernel-on-a-block-device-driver)

Good luck!

---

