---
title: "Ruby on Rails NoMethodError"
date: 2009-05-24
forum: Programming Talk
---

### Post by vhenry on 2009-05-24
Creating my first rails app, and having problem trying to execute save of new movie object. 

NoMethodError: You have a nil object when you didn't expect it!
You might have expected an instance of ActiveRecord::Base.
The error occurred while evaluating nil.save

Any ideas what's causing this error?

controller code:
class MoviesController < ApplicationController
  # GET /movies
  # GET /movies.xml
  
  before_filter :find_movie,
    :only => [:show, :edit, :update, :destroy]
    
  def index
    @movies = Movie.all

    respond_to do |format|
      format.html # index.html.erb
      format.xml  { render :xml => @movies }
    end
  end

  # GET /movies/1
  # GET /movies/1.xml
  def show
      respond_to do |format|
      format.html # show.html.erb
      format.xml  { render :xml => @movie }
    end
  end

  # GET /movies/new
  # GET /movies/new.xml
  def new
    @movie = Movie.new

    respond_to do |format|
      format.html # new.html.erb
      format.xml  { render :xml => @movie }
    end
  end

  # GET /movies/1/edit
  def edit
    @movie = Movie.find(params[:id])
  end

  # POST /movies
  # POST /movies.xml
  def create
    respond_to do |format|
      if @movie.save
        flash[:notice] = 'Movie was successfully created.'
        format.html { redirect_to(@movie) }
        format.xml  { render :xml => @movie, :status => :created, :location => @movie }
      else
        format.html { render :action => "new" }
        format.xml  { render :xml => @movie.errors, :status => :unprocessable_entity }
      end
    end
  end

  # PUT /movies/1
  # PUT /movies/1.xml
  def update
    respond_to do |format|
      if @movie.update_attributes(params[:movie])
        flash[:notice] = 'Movie was successfully updated.'
        format.html { redirect_to(@movie) }
        format.xml  { head :ok }
      else
        format.html { render :action => "edit" }
        format.xml  { render :xml => @movie.errors, :status => :unprocessable_entity }
      end
    end
  end

  # DELETE /movies/1
  # DELETE /movies/1.xml
 ...

---

### Post by soltanis on 2009-05-25
Please format your code in ```
 tags.

Example:
[code]
this.is_some(code);
this {
    is();
    some.properly.indented_code = 0;
}

```

---

### Post by vhenry on 2009-05-25
resubmitting with code tags. 

```
class MoviesController < ApplicationController
  # GET /movies
  # GET /movies.xml
  
  before_filter :find_movie,
    :only => [:show, :edit, :update, :destroy]
    
  def index
    @movies = Movie.all

    respond_to do |format|
      format.html # index.html.erb
      format.xml  { render :xml => @movies }
    end
  end

  # GET /movies/1
  # GET /movies/1.xml
  def show
      respond_to do |format|
      format.html # show.html.erb
      format.xml  { render :xml => @movie }
    end
  end

  # GET /movies/new
  # GET /movies/new.xml
  def new
    @movie = Movie.new

    respond_to do |format|
      format.html # new.html.erb
      format.xml  { render :xml => @movie }
    end
  end

  # GET /movies/1/edit
  def edit
    @movie = Movie.find(params[:id])
  end

  # POST /movies
  # POST /movies.xml
  def create
    respond_to do |format|
      if @movie.save
        flash[:notice] = 'Movie was successfully created.'
        format.html { redirect_to(@movie) }
        format.xml  { render :xml => @movie, :status => :created, :location => @movie }
      else
        format.html { render :action => "new" }
        format.xml  { render :xml => @movie.errors, :status => :unprocessable_entity }
      end
    end
  end

  # PUT /movies/1
  # PUT /movies/1.xml
  def update
    respond_to do |format|
      if @movie.update_attributes(params[:movie])
        flash[:notice] = 'Movie was successfully updated.'
        format.html { redirect_to(@movie) }
        format.xml  { head :ok }
      else
        format.html { render :action => "edit" }
        format.xml  { render :xml => @movie.errors, :status => :unprocessable_entity }
      end
    end
  end

  # DELETE /movies/1
  # DELETE /movies/1.xml
  def destroy
   
    @movie.destroy

    respond_to do |format|
      format.html { redirect_to(movies_url) }
      format.xml  { head :ok }
    end
  end
  
  private
    def find_movie
      @movie = Movie.find(params[:id])
    end
end
```

---

### Post by crush304 on 2009-05-25
```
  # POST /movies
  # POST /movies.xml
  def create
    respond_to do |format|
      if @movie.save
        flash[:notice] = 'Movie was successfully created.'
```

it looks like you are using @movie before you initialize it

try something like

```
  # POST /movies
  # POST /movies.xml
  def create
    **@movie=Movie.new(params[:movie])**
    respond_to do |format|
      if @movie.save
        flash[:notice] = 'Movie was successfully created.'
```

---

### Post by vhenry on 2009-05-26
that did the trick - true noob mistake. :D

---

