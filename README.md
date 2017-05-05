# WikipediaCodingLanguageOccurrence
Analyzing frequencies of coding language names mentioned in Wikipedia articles.  
This is the homework assignment from course "Big Data Analysis with Scala and Spark."  
The following coding languages are concerned:  
["JavaScript", "Java", "PHP", "Python", "C#", "C++", "Ruby", "CSS", "Objective-C", "Perl", "Scala", "Haskell", "MATLAB", "Clojure", "Groovy".]  
The algorithm first create an RDD with the input file [wikipedia](http://alaska.epfl.ch/~dockermoocs/bigdata/wikipedia.dat).  
Note that here the frequencies is not the total number of time a word occurs but the total number of articles that mentions a word.  
Example: ["Scala is smarter than Java and Java is smater than C.", "I love C.", "Spark supports Python too."]  
Then we should have [(C, 2), (Scala, 1), (Java, 1), (Python, 1)]  
Scala is counted once even though it appears twice in the first article; and C appears on the first and second articles so its frequency is 2.  
It computes the ranking of occurrences for coding language listed above with three different techniques:  
- Naive approach: gets occurrence number of each language and sorts the <language, occurrence> pairs.  
- Inverted index ranking: creates a <language, article> pair whenever the language is found on an article; group by key (language).
Each key's value will be the list of all articles containing the key. Transforming it to RDD of key and list size and do sorting.  
- Reduced by Key: directly invokes the reduceByKey.
