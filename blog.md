---
layout: page
title: Blog
permalink: /blog/
---

Hi my name is Robert!
<div class="cf frame">
    {% for post in paginator.posts %}
      <article class="post" itemscope itemtype="http://schema.org/BlogPosting" role="article">
        <div class="article-item">
          <header class="post-header">
            <h2 class="post-title" itemprop="name"><a href="{{ site.baseurl }}{{ post.url | remove: '/'}}" itemprop="url">{{ post.title }}</a></h2>
          </header>
          <section class="post-excerpt" itemprop="description">
            <p class="post-description">{{ post.excerpt | strip_html | truncatewords: 50 }}</p>
          </section>
          <div class="post-meta">
            {% for author in site.data.authors %}
              {% if author[1].username == post.author %}
                {% if author[1].assets %}<amp-img width="24" height="24" class="author-thumb" layout="responsive" src="{{ site.baseurl }}{{author[1].assets}}" alt="{{author[1].name}}"/></amp-img>{% endif %}
                <a href="{{site.baseurl}}authors/#{{author[1].username}}">{{author[1].name}}</a>
              {% endif %}
            {% endfor %}

            {% if post.tags.size > 0 %}
                in
                {% for tag in post.tags %}
                    {% if forloop.index == post.tags.size %}
                       <a href='{{site.baseurl}}tags/#{{tag}}'>{{ tag | capitalize }}</a>
                    {% else %}
                       <a href='{{site.baseurl}}tags/#{{tag}}'>{{ tag | capitalize }}</a>,
                    {% endif %}
                {% endfor %}
            {% endif %}
              <time class="post-date" datetime="{{ post.date | date:'%Y-%m-%d' }}">{{ post.date | date_to_string }}</time>
          </div>
        </div>
      </article>
    {% endfor %}
  </div>
