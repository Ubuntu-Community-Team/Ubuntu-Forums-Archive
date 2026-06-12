---
title: "[C++] Unique float tuples in an array"
date: 2013-12-27
forum: Programming Talk
---

### Post by kangaba on 2013-12-27
Hi,
In C++ I got an array of floats each next 3 floats representing the coords of a point.
Before adding another tuple of 3 floats I must make sure the array doesn't contain a similar tuple.
How should I do it?

Currently, before adding a new tuple, I just loop thru the array in search of a similar tuple, which is (highly) inefficient as the loop grows larger.
Can one use a "map" or "hash table"..?


The context:
An icosahedron being transformed into a sphere, without duplicating existing point coords. [Basic explanation]("http://blog.andreaskahler.com/2009/06/creating-icosphere-mesh-in-code.html").

My implementation of IcoSphere.cpp:
[PHP]
#include "IcoSphere.hpp"

#include "../Context.hpp"
#include "../mgl.hpp"

#include <cmath>
#include <iostream>
#include <cstdlib>

const float t = (1.0f + sqrt(5.0)) / 2.0f;

namespace mgl        {
namespace geom        {

IcoSphere::IcoSphere()
{
    ctx_ = NULL;
}

IcoSphere::~IcoSphere()
{
    delete coords_;
    delete indices_;
    ctx_->glDeleteBuffers(2, buf_ids_);
}

void
IcoSphere::Gen(mgl::Context *cx, const GLuint v, const int level)
{
    ctx_ = cx;
    
    if (level_ == -1) {
        vao_ = v;
        level_ = 0;
        ctx_->glGenBuffers(2, buf_ids_);
        indices_ = new std::vector<GLushort>();
        coords_ = new std::vector<float>();
    }
    
    indices_->clear();
    coords_->clear();
    const float s = 1.0f;
    
    float coords[] = {
        -s, t, 0,
        s, t, 0,
        -s, -t, 0,
        
        s, -t, 0,
        0, -s, t,
        0, s, t,
        
        0, -s, -t,
        0, s, -t,
        t, 0, -s,
        
        t, 0, s,
        -t, 0, -s,
        -t, 0, s
    };
    
    size_t count = (sizeof coords) / sizeof(float);
    mgl::geom::Add(coords, count, coords_);
    
    GLushort indices[] = {
        0, 11, 5,
        0, 5, 1,
        0, 1, 7,
        0, 7, 10,
        
        0, 10, 11,
        1, 5, 9,
        5, 11, 4,
        11, 10, 2,
        
        10, 7, 6,
        7, 1, 8,
        3, 9, 4,
        3, 4, 2,
        
        3, 2, 6,
        3, 6, 8,
        3, 8, 9,
        4, 9, 5,
        
        2, 4, 11,
        6, 2, 10,
        8, 6, 7,
        9, 8, 1
    };
    
    count = sizeof indices / sizeof(GLushort);
    for(int i=0; i<count; i++) {
        indices_->push_back(indices[i]);
    }
    
    const int kRealLevel = (level > kMaxLevel) ? kMaxLevel : level;
    for(int i=0; i<kRealLevel; i++) {
        Subdivide();
    }
    
    //==> vao
    ctx_->glBindVertexArray(vao_);
    
    ctx_->glBindBuffer(GL_ARRAY_BUFFER, buf_ids_[0]);
    ctx_->glBufferData(GL_ARRAY_BUFFER, coords_->size() * sizeof(float),
        coords_->data(), GL_STATIC_DRAW);
    
    ctx_->glBindBuffer(GL_ELEMENT_ARRAY_BUFFER, buf_ids_[1]);
    ctx_->glBufferData(GL_ELEMENT_ARRAY_BUFFER,
        indices_->size() * sizeof(GLushort), indices_->data(), GL_STATIC_DRAW);
    
    ctx_->glEnableVertexAttribArray(mgl::attr::kPos);
    ctx_->glVertexAttribPointer(mgl::attr::kPos, 3, GL_FLOAT,
        GL_FALSE, 0, (void*)0);
    
    //<== vao
    ctx_->glBindVertexArray(0); //unbind vao
    
    // must be at the end
    level_ = kRealLevel;
    
    /**
    const float coords_count = coords_->size();
    const float points_count = coords_count / 3;
    const float ind_count = indices_count();
    
    std::cout << "level: " << level_ << ", coords: " << coords_count
        << ", points: " << points_count << ", indices: " << ind_count
        << std::endl;
    **/
}

void
IcoSphere::Subdivide()
{
    auto *indices = new std::vector<GLushort>();
    const int kIndicesCount = indices_->size();
    // indices into the coord array
    int pind1, pind2, pind3;
    GLushort ol1, ol2, ol3, nu1, nu2, nu3;
    
    for(int i=0; i<kIndicesCount; i+=3)
    {
        ol1 = (*indices_)[i];
        ol2 = (*indices_)[i + 1];
        ol3 = (*indices_)[i + 2];
        
        pind1 = ol1 * 3;
        pind2 = ol2 * 3;
        pind3 = ol3 * 3;
        
        nu1 = mgl::geom::AddMidPoint(pind1, pind2, coords_);
        nu2 = mgl::geom::AddMidPoint(pind2, pind3, coords_);
        nu3 = mgl::geom::AddMidPoint(pind3, pind1, coords_);
        
        // trig 1
        indices->push_back(ol1);
        indices->push_back(nu1);
        indices->push_back(nu3);
        
        // trig 2
        indices->push_back(ol2);
        indices->push_back(nu2);
        indices->push_back(nu1);
        
        // trig 3
        indices->push_back(nu1);
        indices->push_back(nu2);
        indices->push_back(nu3);
        
        // trig 4
        indices->push_back(nu2);
        indices->push_back(ol3);
        indices->push_back(nu3);
    }
    
    delete indices_;
    indices_ = indices;
}

void
Add(float *data, const size_t count, std::vector<float> *v)
{
    float x, y, z;
    
    for(int i=0; i<count; i+=3)
    {
        x = data[i];
        y = data[i+1];
        z = data[i+2];
        
        mgl::Normalize(x, y, z);
        
        v->push_back(x);
        v->push_back(y);
        v->push_back(z);
    }
}

GLushort
AddMidPoint(int i1, int i2, std::vector<float> *v)
{
    const float *a = v->data();
    
    float x = (a[i1] + a[i2]) / 2.0f;
    float y = (a[i1+1] + a[i2+1]) / 2.0f;
    float z = (a[i1+2] + a[i2+2]) / 2.0f;
    
    mgl::Normalize(x, y, z);
    
    //==> check point coord already exists
    static const float kErr = 0.001f;
    const int kSize = v->size();
    for(int i=0; i<kSize; i+=3) {
        
        if (fabs(a[i] - x) < kErr && fabs(a[i+1] - y) < kErr &&
            fabs(a[i+2] - z) < kErr)
        {
            // exists, return its index
            return GLushort(i/3);
        }
    }
    //<== check point coord already exists
    
    v->push_back(x);
    v->push_back(y);
    v->push_back(z);
    
    return GLushort(kSize / 3);
}

} // namespace geom
} // namespace mgl

[/PHP]

IcoSphere.hpp:
[PHP]#ifndef MGL_GEOM_ICOSPHERE_HPP_
#define MGL_GEOM_ICOSPHERE_HPP_

#include <mtl/err.hpp>
#include <GL/gl.h>
#include <vector>

#include "../declare.hxx"

namespace mgl        {
namespace geom        {

class IcoSphere
{
public:
    IcoSphere();
    virtual ~IcoSphere();
    
    void
    Gen(mgl::Context *ctx, const GLuint vao, int level);
    
    std::vector<GLushort>*
    indices() { return indices_; }
    
    int
    indices_count() { return indices_->size(); }
    
    int
    level() { return level_; }
    
    void
    Subdivide();
    
    static const int kMaxLevel = 3;
    
protected:
    void
    Init();
    
private:
    DISALLOW_COPY_AND_ASSIGN(IcoSphere);
    
    /** 1st buf for coords, 2nd for indices **/
    GLuint                    buf_ids_[2];
    std::vector<float>        *coords_;
    mgl::Context            *ctx_ = NULL;
    std::vector<GLushort>    *indices_;
    /** -1 means no sphere generated yet **/
    int                        level_ = -1;
    GLuint                    vao_;
};

void
Add(float *data, const size_t count, std::vector<float> *v);

GLushort
AddMidPoint(int i1, int i2, std::vector<float> *v);

} // namespace geom
} // namespace mgl

#endif

[/PHP]

---

### Post by ofnuts on 2013-12-27
Since you are dealing with floating point numbers, I would be weary of using anything that works on strict equality such as a map or a hash table.

I would add some way to retrieve a triplet quickly based on its first coordinate, for instance have a binary/AVL tree where the data is a pointer to (or the index of) the first coordinate of a triplet, so you can quickly find the triplets with the same first coordinate (within some epsilon). When you have them you can still test the other two coordinates for equality (within some epsilon) with the last two coordinates of your new point, or use a distance criterion between the two points (in which case the epsilon used to search the tree is the minimum distance).

---

