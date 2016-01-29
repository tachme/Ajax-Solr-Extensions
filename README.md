# Ajax-Solr-Extensions
Extensions to the Ajax-Solr JavaScript framework for creating search user interfaces to Apache Solr.

[AJAX Solr](https://github.com/evolvingweb/ajax-solr) is a JavaScript library for creating user interfaces to the popular [Apache Solr](http://lucene.apache.org/solr/) search engine. I have successfully used Ajax-Solr to create several internal web interfaces to Solr at my company [Bristol-Myers Squibb](http://www.bms.com). As part of this I created some extensions and enhancements to Ajax-Solr that I feel would be valuable to other Ajax-Solr users and thus I am releasing those here. Specifically, I created two new widgets for viewing and querying facets, and I created an enhanced version of Ajax-Solr's ResultWidget.js:

* **MultiSelectWidget.js** This is a useful alternative to Ajax-Solr's TagcloudWidget.js and enables faceted filtering similar to many popular e-commerce sites such as Amazon.com, Walmart.com, etc. (i.e. facet values in ordered lists selected by checking checkboxes). Whereas TagcloudWidget.js shows facet values as a tag cloud and users can select a single facet value (and only a single facet value) by clicking on it, MultiSelectWidget.js shows the top facet values in a list ordered by count with checkboxes that the user can check to choose facet values (and more than one facet value for a facet can be selected, resulting in an "OR" query for the selected values). In addition to showing the top (e.g. top 20) facet values and allowing them to be easily selected by checking a checkbox, it also has a [jQuery UI autocomplete](https://jqueryui.com/autocomplete/) where the user can choose any facet value (JSONP queries to Solr are done based on the users typed text in the autocomplete). Finally, it also supports binned ranges for numerical values (e.g. "0 TO 24", "25 TO 49", etc.), allowing sorting of the facet values based on the ranges instead of the counts (which can be more intuitive). Here is a screen snapshot of MultiSelectWidget.js:   
![Image of MultiSelectWidget](http://biogit.pri.bms.com/github-enterprise-assets/0000/0031/0000/0004/3626c418-beb2-11e5-92d9-c4ada4c0589c.png)
* **RangeWidget.js** For numerical fields, this widget allows users to add a range query (e.g. "23 TO 57", etc.) on the field to the overall Solr query by either moving 2 sliders on superimposed [HTML 5 range input elements](http://www.w3schools.com/jsref/dom_obj_range.asp), or by directly entering (into input text boxes) the left and right range values. Here is a screen snapshot example of RangeWidget.js:   
![Image of RangeWidget](http://biogit.pri.bms.com/github-enterprise-assets/0000/0031/0000/0005/380ac4e6-beb2-11e5-9f17-0b85035b7d98.png)
* **ResultWidget.js**
I created an enhanced version of Ajax-Solr's ResultWidget.js that supports contextual highlighted matches (using [Solr's highlighting functionality](https://wiki.apache.org/solr/HighlightingParameters)) and NOT showing the entire result set before any search is entered (which can be confusing, i.e. "why am I getting results when I haven't even entered a search yet??"). Note that a small change to PagerWidget.js was also needed for not showing the entire result set before any query is entered. Here is a screen snapshot showing highlighting snippets: ![Image of highlighting snippets](http://biogit.pri.bms.com/github-enterprise-assets/0000/0031/0000/0007/54bc30a4-bebf-11e5-9add-360e02bde3fb.png)

[Here](http://buddyroo30.github.io/Ajax-Solr-Extensions/) is a demo site (for the same reuters index used by Ajax-Solr) showing the MultiSelectWidget.js and ResultWidget.js.