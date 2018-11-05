# Progress Bar

### 동작 시현
![](/screenshot/progress_bar.gif)

* AysncTask를 사용하여 ProgressBar 구현하기
````java
 new AsyncTask<Void, Integer, Boolean>() {
        @Override
        protected void onPreExecute() {
            super.onPreExecute();
        }

        @Override
        protected Boolean doInBackground(Void... voids) {
            for(int i = 0; i <= 100; ++i) {
                try { Thread.sleep(200); } catch(Exception e) { e.printStackTrace(); }
                publishProgress(i);
            }
            return null;
        }

        @Override
        protected void onProgressUpdate(Integer... values) {
            super.onProgressUpdate(values);
            textView.setText(values[0] + "%");
            bar.setProgress(values[0]);
        }

        @Override
        protected void onPostExecute(Boolean aBoolean) {
            super.onPostExecute(aBoolean);
        }
    }.execute();
}
````
