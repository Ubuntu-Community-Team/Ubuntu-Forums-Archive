---
title: "glGetUniformLocation not working"
date: 2008-05-27
forum: Programming Talk
---

### Post by gorded on 2008-05-27
I use glGetUniformLocation to find to addresses of two sampler2d in my fragment shader, i find the first adress as being zero but the second adress is -1 and i know i am using the right name and the uniform is being used in the shader. The same thing happens with my attribute location.

```
// [Vertex Shader]

varying vec3 eye;
varying vec3 light;

attribute vec3 tangent;

void main(void) {
	gl_FrontColor = gl_Color;
	gl_Position = gl_ModelViewProjectionMatrix * gl_Vertex;
	gl_TexCoord[0] = gl_MultiTexCoord0;
	
	vec3 n = normalize(gl_NormalMatrix * gl_Normal);
	vec3 t = normalize(gl_NormalMatrix * tangent);
	vec3 b = cross(n, t);
	
	vec3 vertex = vec3(gl_ModelViewMatrix * gl_Vertex),
		temp = gl_LightSource[0].position.xyz - vertex;
	
	light.x = dot(temp, t);
	light.y = dot(temp, b);
	light.z = dot(temp, n);
	light = normalize(light);
	
	temp = -vertex;
	
	eye.x = dot(temp, t);
	eye.y = dot(temp, b);
	eye.z = dot(temp, n);
	eye = normalize(eye);
}
```

```
// [Fragment Shader]

varying vec3 eye;
varying vec3 light;

uniform sampler2D textMap;
uniform sampler2D normMap;

void main(void) {
	vec4 color = texture2D(textMap, gl_TexCoord[0].st);
	vec3 normal = normalize(2.0 * texture2D(normMap, gl_TexCoord[0].st).xyz - 1.0);
	
	// Ambient Light :: la = Al * Am
	vec4 ambient = gl_LightSource[0].ambient * gl_FrontMaterial.ambient;
	
	// Diffuse Light :: ld = Dl * Dm * LambertTerm
	float lambert = max(dot(normal, light), 0.0);
	vec4 diffuse = gl_LightSource[0].ambient * gl_FrontMaterial.diffuse * lambert;
	
	// Specular Light :: ls = Sl * Sm * pow(max())
	vec4 specular = pow(max(dot(reflect(-light,normal), eye),0.0) ,gl_FrontMaterial.shininess) 
		* gl_LightSource[0].specular * gl_FrontMaterial.specular;
	
	gl_FragColor = ambient*color + diffuse*color + specular;
	gl_FragColor = color;
}
```

```
	glLinkProgram(program);
	
	printProgramInfoLog(program);
	
	glUseProgram(program);
	
	vertTan = glGetAttribLocation(program,"tangent");
	
	fragBMap = glGetUniformLocation(program, "normMap");
	fragTMap = glGetUniformLocation(program, "textMap");
	
	fprintf(stderr, "%d %d %d", fragTMap, fragBMap, vertTan);
```

Any ideas ??

---

