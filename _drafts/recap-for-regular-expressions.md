---
title: "r're(gular) expre(s+)ions' "
excerpt: "Pretty boring and generic blabbering about regular exressions"
author_profile: false
---

## Intro

Recently I saw a tweet of Jake Wharton, and the idea it represented really clicked with
me since I started to experience this more and more. Here is the tweet:

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">The opposite of &quot;it&#39;s like riding a bike&quot; is &quot;it&#39;s like programming in bash&quot;.<br><br>A phrase which means that no matter how many times you do something, you will have to re-learn it every single time.</p>&mdash; Jake Wharton (@JakeWharton) <a href="https://twitter.com/JakeWharton/status/1334177665356587008?ref_src=twsrc%5Etfw">December 2, 2020</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 

I think this concept is true in different levels for most of things. Other than bash programming (which
I needed recently to automate some of the git related stuff at work) the second most likely culprit is
regular expressions. Basically it is a magical way to work with text using pattern matching. I thought If
I write a lengthy enough post on this Sunday evening with Covid lockdown keeping me company, I would no longer
need to relearn it every time I need it, and failing to automate things that would usually take couple of hours
maybe trim down to couple of.. well tens of minutes maybe, let's be realistic :).

Almost every language has a specific library, or a package for regular expressions. Since I use it for
mostly in python scripts and machine learning stuff, I will be giving examples using Python's **re** module.
But the general rules about the patterns and the matching characters should not change that much.
Here is a generic example to use regular expressions in Python:

{% highlight python%}
import re
pattern = re.compile('ab\*')
{%endhighlight%}

I will divide this post into several sections so that it is easy to follow along. These are

- Special Metacharacters
- Core Matching Rules
- Lookaheads for early exit

## Special Metacharacters

We'll start with the basic metacharacters. Most letters and characters will simply match themselves.
Some of the characters are considered as _metacharacters_, they affect the portion of the regular expression
in a certain way to match the required pattern.

| Characters | What they do                                                                                           |
| ---------- | ------------------------------------------------------------------------------------------------------ |
| .          | Matches any character except newline                                                                   |
| [ ]        | Used for specifying the character class, Also used for range of characters [abc] or [a-z]              |
| ^          | used for complementing in the range brackets [^5]                                                      |
| $          | Matches the end of the line. Acts as a normal character inside []                                      |
| \*         | Used for representing 0 or more characters. Use with \\ to match itself                                |
| \\         | Is used with other metachars and allow using special characters without invoking their special meaning |
| +          | Used for representing 1 or more characters. Use with \\ to match itself                                |
| { }        | Used to define exact repetition or a range of repetition of a character or a character set. ex: a{2,5} |
| ( )        | Used to group the refular expressions                                                                  |

## Core Matching Rules

Next there are sequences. They represent a certain character sets for easy matching beginning with \\, such as set of digits,
the set of letters or the set of anything that isn't whitespace. These are the most common sequences:

{% highlight python%}
import re

#Matches any decimal digit, equivalent to [0-9]
pattern = re.compile(r'\d')
#Matches any non-digit character, equivalent to [^0-9]
pattern = re.compile(r'\D')
#Matches any whitespace character, equivalent to [\t\n\r\f\v]
pattern = re.compile(r'\s')
#Matches any non white space character [^ \t\n\r\f\v]
pattern = re.compile(r'\S')
#Matches any alhanumeric character, equivalent to [a-zA-Z0-9_]
pattern = re.compile(r'\w')
#Matches any non-alphanumeric character, [^ a-zA-Z0-9\_]
pattern = re.compile(r'\W')
{%endhighlight%}

These sequences can be included inside a character class.

## Lookaheads for early exit

---

References

- [Official Python docs](https://docs.python.org/3/howto/regex.html)
