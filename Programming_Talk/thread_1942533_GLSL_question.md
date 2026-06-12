---
title: "GLSL question"
date: 2012-03-17
forum: Programming Talk
---

### Post by t1497f35 on 2012-03-17
Hi,
Why is the author computing a "currTime" and not just using "time" as is?
I put "time" instead of "currTime" for cos and sin and it seems to work fine..

See [Example 3.6. Offset Computing Vertex Shader]("http://www.arcsynthesis.org/gltut/Positioning/Tut03%20More%20Power%20To%20The%20Shaders.html")

```

#version 330

layout(location = 0) in vec4 position;
uniform float loopDuration;
uniform float time;

void main()
{
    float timeScale = 3.14159f * 2.0f / loopDuration;
    
    float currTime = mod(time, loopDuration);
    vec4 totalOffset = vec4(
        cos(currTime * timeScale) * 0.5f,
        sin(currTime * timeScale) * 0.5f,
        0.0f,
        0.0f);
    
    gl_Position = position + totalOffset;
}

```

---

### Post by JDShu on 2012-03-18
I assume it's so that loopDuration actually does something.

---

