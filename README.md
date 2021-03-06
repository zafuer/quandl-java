quandl-java
===========
 [![githalytics.com alpha](https://cruel-carlota.pagodabox.com/66c2b522d67dfd66cc5e445fc32976ee "githalytics.com")](http://githalytics.com/github.com/iamtrask)
This is a java api for the quandl dataservice. It's goal is to make it easy for you to use Quandl's data for a java application.

Our first step is to open a connection to quandl using an api key. This connection will facilitate the creation of dataset objects (dataset downloads).

Login to Quandl and go to http://www.quandl.com/users/edit

Click "API" and you will see your key. You will want to use this as the rate limits are higher if you are using a key.

        //open connection with key
        QuandlConnection q = new QuandlConnection("my key");

If you don't provide a key (or supply a bad one), you can still open a connection. You'll just be notified that your rate limit is significantly smaller.

        //open connection without key
        QuandlConnection r = new QuandlConnection();

QDataset is the basic quandl-java object. It downloads data in JSON form and converts it into a java object. The minimal setting you must supply is the "Quandle Code"... which is available on Quandl dataset pages.

        //get dataset from keyrange
        QDataset data1 = q.getDataset("PRAGUESE/PX");

        //get dataset between two sets of dates... don't forget to use this format for the date.
        QDataset data2 = q.getDatasetBetweenDates("PRAGUESE/PX","2012-01-01","2012-11-26");

This version lets you set your custom parameters. You can pick from any parameters on the Quandl API page. http://www.quandl.com/api

        //get dataset with custom parameters
        HashMap<String, String> params = new HashMap<String, String>();
        params.put("trim_start","2012-09-30");
        params.put("code","PX");
        params.put("source_code","PRAGUESE");
        QDataset data3 = q.getDatasetWithParams(params);

A few examples of extracting the data from a QDataset.

        //get Dataset as array matrix
        ArrayList<ArrayList<String>> data3Matrix = data3.getArrayMatrix();

        //get Dataset as String Matrix
        String[][] data3StringMatrix = data3.getStringMatrix();
        
        
       
