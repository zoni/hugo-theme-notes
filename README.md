# Sidey

This is a Hugo port of the [sidey] theme from Ronalds Vilciņš.

## Search

To make the built-in [lunr]-based search functionality work, follow these steps.

### Configure JSON index

In your Hugo configuration, enable the JSON output format for `/index.json` using something like the following (this example uses TOML):

```toml
[outputFormats]
	[outputFormats.SearchIndex]
	baseName = "index"
	mediaType = "application/json"

[outputs]
home = ["HTML", "SearchIndex"]
```

### Create search page

Create `search.md` at the root of your `content` folder with these contents:

```
---
title: Search this site
---

# Search

<div id="search-container">
  <form id="search-form" action="{{< ref "/search" >}}">
    <input name="q" id="search-input" type="text" class="search_input search-query ui-autocomplete-input" placeholder="Search notes" autocomplete="off">
  </form>
</div>

<template id="search-result" hidden>
  <article class="content post">
    <h3 class="search-result-title"><a class="search-result-title-ref"></a></h2>
    <summary class="search-result-summary"></summary>
  </article>
</template>

<div id="search-results-container"></div>
```

This will make the search page available at `/search`.

[sidey]: https://github.com/ronv/sidey
[lunr]: https://lunrjs.com/
