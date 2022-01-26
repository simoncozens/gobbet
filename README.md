# TownCrier - Random news articles in any language

Wikinews is a wonderful free source of long-form text in a variety of world languages. TownCrier provides you with access to words, sentences and paragraphs taken from Wikinews articles in any of its supported languages. This can be used as filler text for type specimens, web layouts, etc.

## Example usage

```python

from towncrier import get_news, unicode_ranges

words, headlines, paragraphs = get_news("el") # ISO language code

# words is a Wordlist object; like Counter, but with a few more methods
words = (
    words.filter_popularity(2) # Only words which occur >=2 times
         .filter_length(5)     # ... of five letters or more ...
         .filter_unicodes(unicode_ranges["Greek"]) # .. in Greek script
)

# Want to find some kerning pair words?
bigrams = words.bigrams()
# bigrams['οώ'] === {'προώθησε', 'προώθηση', 'προώθησης', 'προώρων'}

# headlines and paragraphs are just lists, but...
from towncrier import filter_length, filter_unicodes

renderable = filter_unicodes(headlines, [font.getBestCmap().keys()])
```

## License

TownCrier was written by Simon Cozens. See [LICENSE](LICENSE) for the terms of this library.

Note that Wikinews text is provided under the [CC-BY 2.5](https://creativecommons.org/licenses/by/2.5/) license, and your application must comply with the terms of that license in its use of the content.
