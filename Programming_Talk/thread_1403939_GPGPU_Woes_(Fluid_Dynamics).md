---
title: "GPGPU Woes (Fluid Dynamics)"
date: 2010-02-10
forum: Programming Talk
---

### Post by kiplingw on 2010-02-10
I have a 2D array allocated as a 1D array (pGridLocations). This array represents the points on a flat 2D grid. Each point is a pair of GLuints (e.g. bottom left is (0,0), top right is point (width,height)). They are all integral values.

I want to pass this array of pairs to my shader where I do some fancy calculations and write out the results to a texture (bound via FBO) of the same width / height as the grid dimensions. Each texel (I use only single channel) contains a Z-displacement value of the wave at that position on surface.

I am finding though that getting my pairs into the shader is very difficult and I've gone through a lot of documentation and cannot seem to get it to work. Whether the glDrawArrays is called or not, the buffer seems to contain the same junk.

Here is where I initialize the pairs:
```

    // Initialize grid location pairs...

        // Calculate required storage space for all location pairs...
        GLuint const Storage = m_Width * m_Height * sizeof(GLuint) * 2;

        // Allocate...
        GLuint *pGridLocations = (GLuint *) malloc(Storage);

        // Initialize vertex ordinals across the grid...
        for(GLuint CurrentY = 0; CurrentY &lt; m_Height; ++CurrentY)
            for(GLuint CurrentX = 0; CurrentX &lt; m_Width; ++CurrentX)
            {
                // Calculate current location...
                GLuint *pCurrentLocation =
                    pGridLocations + (2 * ((CurrentY * m_Width) + CurrentX));

                // Store grid index...
                pCurrentLocation[0] = CurrentX;
                pCurrentLocation[1] = CurrentY;
            }

        // Initialize vertex buffer object with vertex pairs...

            // Allocate...
            glGenBuffers(1, &m_VBO_GridLocations);

            // Select...
            glBindBuffer(GL_ARRAY_BUFFER, m_VBO_GridLocations);

            // Commit grid indices to card...
            glBufferData(GL_ARRAY_BUFFER, Storage, pGridLocations, GL_STATIC_DRAW);

            // Associate data with generic vertex attribute...
            glVertexAttribIPointer(m_GVA_GridLocations, 2, GL_UNSIGNED_INT, 0, BufferOffset(0));

```

Here is where I try to pass the data to the shader:
```

    // Redirect rendering through our framebuffer object...
    glBindFramebuffer(GL_FRAMEBUFFER, m_FrameBufferObject);

        // Check for OpenGL errors...
        PrintOpenGLErrors();

    // Make sure data written to texture replaces and doesn't just modulate...
    glTexEnvi(GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, GL_REPLACE);

    // Send grid location data to program...

        // Install program...
        glUseProgram(m_PO_EvaluateWaves);

        // Select the Z map texture...
        glBindTexture(GL_TEXTURE_2D, m_ZMaps_TextureID[0]);

        // Enable required vertex arrays...
        glEnableVertexAttribArray(m_GVA_GridLocations);

        // Select the grid indices...
        glBindBuffer(GL_ARRAY_BUFFER, m_VBO_GridLocations);

        // Commit data to shader...
        glDrawArrays(GL_POINTS, 0, m_Width * m_Height);

        // Disable required vertex arrays...
        glDisableVertexAttribArray(m_GVA_GridLocations);

```

vertex shader:
```

// We want at least GLSL 1.50...
#version 150

// Input variables...

    // Grid location...
    in uvec2            GridLocation;

// Variables for the fragment shader, none of which need be interpolated...

    // Grid location...
    flat out uvec2      Location;

// Entry point...
void main()
{
    Location = GridLocation;
}

```

And the fragment shader:
```

// We want at least GLSL 1.50...
#version 150

// Input variables...

    // Grid location...
    flat in uvec2   Location;

// Output variables...

    // Z-displacement...
    out float       StoredZ_0;

// Entry point...
void main()
{
    float temp = min(float(Location.x), 0.5);
    temp = max(temp, 0.5);
    StoredZ_0 = temp;
}

```

And it just passes a zero or some other test value on to the fragment shader which then writes it to the logical buffer GL_COLOR_ATTACHMENT0, but nothing happens.

I've been stumped on this for days and any help would be much appreciated.

Kip

---

