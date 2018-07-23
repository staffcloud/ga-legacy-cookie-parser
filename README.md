# GA Legacy Cookie Parser

Once upon a time, people used to parse Google Analytics cookies to retrieve and store user and campaign data in their 
database. Unfortunately, with Universal Analytics (UA), it was not possible to retrieve the GA cookie values anymore, 
since Universal Analytics script does not store relevant data on a cookie but processes it on server side.

This script provides a replacement for environments using Universal Analytics. It includes the old `ga.js`, makes sure 
it runs smoothly besides `analytics.js`, replicates several removed GA functions and provides an interface for 
accessing the data.

**Attention:**
- This script is based on the deprecated `ga.js`, it is very likely that some day it will stop working. 
Nevertheless, it will probably work for some more years since many websites are still actively using old GA versions.
- While I am not a lawyer myself, I suspect that using this script does violate most of Google's TOC as well as most 
countries' data protection laws. I would strongly recommend to inform your users about your tracking activities and 
perform a risk assessment.

If you are looking for a "compliant" solution, have a look at [this](https://github.com/dm-guy/utm-alternative/)
library, it replicates the tracking functionality of Google Analytics. 

# Constructor

* `new GAParser([domains], limitRelevant = true)`

Returns a new instance.

# Methods

* `getInfo()`

Returns an object containing the parsed information.

* `setCookie(name = '_ga-legacy-tracking')`

Sets a cookie containing a JSON string with parsed information.

* `addToForm(formId, inputName = '_ga-legacy-tracking')`

Adds a hidden input to the specified form containing a JSON string with parsed information.

# Usage

```
<!-- Add before </body> -->
<script src="../dist/ga-legacy-cookie-parser.min.js"></script>
<script>
    var parser = new GAParser(['app.local', 'second.com']);
    console.log(parser.getInfo()); // Output info to console
    parser.setCookie(); // Set info to cookie
    parser.addToForm('test-form'); // Add info to form as hidden input
</script>
```

# License

GA Legacy Cookie Parser is free software distributed under the terms of the MIT license.