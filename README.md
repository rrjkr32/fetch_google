# fetch_google
opens all links in first page that appear in a google search results in separate tabs.
       
        import bs4,requests,webbrowser,sys


        str=' '.join(sys.argv[1:])
        webbrowser.open('https://www.google.com/search?q='+str)
        req=requests.get('https://www.google.com/search?q='+str)

        req.raise_for_status()

        soup=bs4.BeautifulSoup(req.text)
        matches=soup.select('.r a')


        for l in matches:
            webbrowser.open('https://www.google.com'+l.get('href'))
