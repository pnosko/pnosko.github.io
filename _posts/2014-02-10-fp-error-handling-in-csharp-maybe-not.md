---
layout: post
title: "Functional Programming 101: L1 - Handling Errors in C#? Maybe."
description: "A panacea to your null-value problems."
modified: 2013-05-31
category: articles
tags: [csharp, error handling, functional programming, monad]
image:
  feature: texture-feature-05.jpg
  credit: Texture Lovers
  creditlink: http://texturelovers.com
---

Are you suffering from a severe case of NullReferenceException? Are you encumbered by the dreaded null-checking condition? Suffer no more, there's a panacea to your null-related woes! Maybe. No, not just maybe, for sheezy there is, that's just how it's called - Maybe. Maybe monad to be correct.
For those of you familiar with the Maybe monad, skip to part 'Maybe Monad aka Option'.

> For the initiates to the Order of Higher-Kinded Types, read some of these:

> Aditya Bhargava's Awesome Explanation With Pictures - http://adit.io/posts/2013-04-17-functors,_applicatives,_and_monads_in_pictures.html
> Mike Hadlow's Introduction - http://mikehadlow.blogspot.co.at/2011/01/monads-in-c1-introduction.html


TE http://blogs.claritycon.com/blog/2013/08/functional-concepts-c/

## The No-Value

So, the problem with `null` appears to be the fact that it isn't a value per se, and so when try to do any operation with it, it blows in your face. Can we do better? What if we had an actual value for the absence of a value (Huh?). You know, something to represent the nothingness. You know, `Nothing`.

## Maybe Monad aka Option

The name Option is sometimes used instead of Maybe, and I chose to do the same.
So, 

{% highlight csharp %}
	public interface IOption<out T>
	{
		bool HasValue { get; }
		T Value { get; }

		TOut Fold<TOut>(Func<T, TOut> onSome, Func<TOut> onNone);
		
		// LINQ operators
		IOption<TOut> Select<TOut>(Func<T, TOut> selector);
		IOption<TOut> SelectMany<TOut>(Func<T, IOption<TOut>> selector);
		IOption<TOut> SelectMany<TIn, TOut>(Func<T, IOption<TIn>> k, Func<T, TIn, TOut> s);
		IOption<T> Where(Func<T, bool> predicate);
	}

{% endhighlight %}


### Body text

Lorem ipsum dolor sit amet, test link adipiscing elit. **This is strong**. Nullam dignissim convallis est. Quisque aliquam.

![Smithsonian Image]({{ site.url }}/images/3953273590_704e3899d5_m.jpg)
{: .image-pull-right}

*This is emphasized*. Donec faucibus. Nunc iaculis suscipit dui. 53 = 125. Water is H2O. Nam sit amet sem. Aliquam libero nisi, imperdiet at, tincidunt nec, gravida vehicula, nisl. The New York Times (That’s a citation). Underline.Maecenas ornare tortor. Donec sed tellus eget sapien fringilla nonummy. Mauris a ante. Suspendisse quam sem, consequat at, commodo vitae, feugiat in, nunc. Morbi imperdiet augue quis tellus.

HTML and CSS are our tools. Mauris a ante. Suspendisse quam sem, consequat at, commodo vitae, feugiat in, nunc. Morbi imperdiet augue quis tellus. Praesent mattis, massa quis luctus fermentum, turpis mi volutpat justo, eu volutpat enim diam eget metus.

### Blockquotes

> Lorem ipsum dolor sit amet, test link adipiscing elit. Nullam dignissim convallis est. Quisque aliquam.

## List Types

### Ordered Lists

1. Item one
   1. sub item one
   2. sub item two
   3. sub item three
2. Item two

### Unordered Lists

* Item one
* Item two
* Item three

## Tables

| Header1 | Header2 | Header3 |
|:--------|:-------:|--------:|
| cell1   | cell2   | cell3   |
| cell4   | cell5   | cell6   |
|----
| cell1   | cell2   | cell3   |
| cell4   | cell5   | cell6   |
|=====
| Foot1   | Foot2   | Foot3
{: rules="groups"}

## Code Snippets

{% highlight css %}
#container {
  float: left;
  margin: 0 -240px 0 0;
  width: 100%;
}
{% endhighlight %}