📌 Slide 1 — Uploading the Dataset
files.upload()


Explanation (for PPT):

Google Colab does not have local files by default.

The files.upload() function opens a file-picker window.

The user selects the CSV file (Phishing URL Dataset), which Colab then loads into the environment.

📌 Slide 2 — Reading the Data
df = pd.read_csv(file_name)


Explanation:

pandas reads the uploaded CSV file.

The dataset is stored in a DataFrame called df, which contains multiple features extracted from URLs (length, domain, TLD, number of subdomains, etc.)

This dataset is used for phishing vs legitimate URL analysis.

📌 Slide 3 — Pie Chart: Phishing vs Legitimate
plt.subplot(2,2,1)
plt.pie(counts, labels=['Legitimate', 'Phishing'], autopct='%1.1f%%')
plt.suptitle("Phishing vs Legitimate")


Explanation:

Displays the distribution of phishing vs legitimate URLs.

counts contains the number of phishing and legitimate samples.

The pie chart quickly shows dataset imbalance.

Useful for understanding whether the model might be biased.

📌 Slide 4 — Scatter Plot: URL Length vs Number of Subdomains
plt.subplot(2,2,2)
plt.scatter(df['URLLength'],df['NoOfSubDomain'],color='blue')
plt.suptitle("URLLength vs NoOfSubDomain")
plt.xlabel("URLLength")
plt.ylabel("NoOfSubDomain")


Explanation:

Shows the relationship between:

URL length

Number of subdomains

Phishing URLs often:

Have more subdomains

Are longer to hide suspicious patterns

Helps visualize suspicious URL behaviors.

📌 Slide 5 — Line Plot: URL Length vs Character Probability
plt.subplot(2,2,3)
plt.plot(df['URLLength'],df['URLCharProb'])
plt.suptitle("URLLength vs URLCharProb")
plt.xlabel("URLLength")
plt.ylabel("URLCharProb")


Explanation:

Plots how the probability of characters in the URL changes with length.

URLCharProb measures how unusual/uncommon the URL characters are.

Phishing URLs often contain:

Random characters

Higher entropy strings

This graph helps detect suspicious patterns.

📌 Slide 6 — Bar Chart: TLD (Top-Level Domain) Frequency
tld_counts = df['TLD'].astype(str).value_counts()
plt.bar(tld_counts.index, tld_counts.values)
plt.suptitle("TLD vs Count")
plt.xlabel("TLD")
plt.ylabel("Count")


Explanation:

Shows which domain endings (TLDs) occur most often.

Phishers often use cheap or uncommon TLDs (e.g., .xyz, .top, .info).

Legitimate sites usually use common TLDs (.com, .org, .net).

Helps identify suspicious domain patterns.

📌 Slide 7 — Overall Purpose

This visualization code helps:

Understand the dataset

Identify phishing trends

Reveal URL patterns used by attackers

Prepare features for machine learning models

