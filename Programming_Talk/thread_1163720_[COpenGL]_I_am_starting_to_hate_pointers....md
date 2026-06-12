---
title: "[C/OpenGL] I am starting to hate pointers..."
date: 2009-05-19
forum: Programming Talk
---

### Post by OutOfReach on 2009-05-19
I'm getting into developing OpenGL apps and I'm working on a wrapper for lib3ds based on another wrapper (which is written in C++). I am trying trying to port-if you will-a function that loads and applies textures. But the compiler keeps giving me this error:
```

error: dereferencing pointer to incomplete type

```
on several lines, the first of which is:
```

if (strcmp(mat->texture1_map.name, model->textureFilenames+x) == 0)

```

Here are relevant parts of the function....
[PHP]
void ApplyTexture(Model *model, Lib3dsMesh *mesh)
{
    ...
    Lib3dsMaterial *mat;
    Lib3dsFace *f;
    /* Loop starts here. */
    ...
    f = &mesh->faceL[i]
    mat = lib3ds_file_material_by_name(model->file, f->material);
    /* Nested loop starts here. */
    if (strcmp(mat->texture1_map.name, (model->textureFilenames+x)) == 0) /* ERROR LINE */
    {
        /* Some stuff here.... */
    }
    /* Nested loop ends main loop continues...*/
    ...
}
[/PHP]
(Error line pointed out)

I can post some more details on request but I am really starting to get annoyed by this problem.

- Thanks.

---

### Post by Tony Flury on 2009-05-19
Not an expert on your library by any means but what it suggests to me is that probably Lib3dsMaterial has been declared, but not defined at that point in the code (so the compiler cannot work out how to do mat->texture1_map.name).

I would check the ordering and contents of the header files and declarations and definitions.

---

### Post by OutOfReach on 2009-05-19
Aha! Thank you that worked :) I re-ordered the lib3ds definitions to go before the GL definitions...very odd

---

### Post by infinities on 2009-05-19
i started appreciating c pointers after i started using java

---

### Post by nvteighen on 2009-05-20
That's really weird... Are you sure you aren't bypassing the API and accessing things you shouldn't? If there's a getter function, use that instead.

If not, then, some header is faulty there... which is unacceptable in C. Maybe you should consider filing a bug report. If header A needs B, then it should include it by itself (of course, the headers have to be guarded against multiple inclusion) and not rely on the programmer being lucky enough to place the headers in the correct order.

---

### Post by CptPicard on 2009-05-20
> **infinities said:**
> i started appreciating c pointers after i started using java

Actually the C pointer is really nothing more than an indirection-value mechanism (an array index to be more exact) that has perfectly good alternatives all other languages that do not specifically do direct-memory access via pointers... I've never understood the "cult of the pointer"; seems like revering a triviality that is elevated simply by lack of perspective ;)

---

