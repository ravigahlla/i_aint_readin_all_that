# stratecheryGPT v2
A summarizer to deal with Stratechery's incessant daily emails

**Problem**: [Stratechery](https://stratechery.com/) is a daily newsletter for technology that can contain valuable content, but the 
daily emails add up as unread after at least a week

**Solution**: Use multiple GPTs to summarize the daily newsletters, increasing quality output, while saving you time

*Program Design*

See [stratecheryGPT-v1-workflow](docs%2FstratecheryGPT-v1-workflow.pdf) for visual

1. From an external server, check daily for emails from Stratechery
2. Summarize the email with [OpenAI's API](https://platform.openai.com/overview), and Llama
3. Send the summary back to my email, along with:
4. An executive summary of all LLMs, keywords, a summary from each LLM, and then the original email

*REQs:*
- a paid account with OpenAI
- a gmail account [with your app pass key setup](https://support.google.com/mail/answer/185833?hl=en)
- you can set this up on your local, but an external server (I used a Raspberry Pi)

*Setup*
1. check out the repo, go to the project directory
2. you need to create your own .config file, containing your credentials (e.g., gmail app pass) in JSON format
3. run 'sudo chmod 600 .config' to give yourself permission to read from the file
4. run 'install .' to run setup.py, and install the right dependencies
5. run 'python3 src/main.py'


***TODO***
- be LLM agnostic (support for OpenAI, Gemini, or a combination of all)
- create a test flag, which will reference variables with various test values (and then a "PROD" state, which will
make it ready for public-use)
- better handle error handling in the try catch code properly (openai.error doesn't exist, so need to find updated version)
- make this server interactive: I can email back a reply, and then get a response, if I want to dig deeper
- setup another email handle (e.g., 'summarizerbot@')?
- split up methods into different related files (or create a class to handle)