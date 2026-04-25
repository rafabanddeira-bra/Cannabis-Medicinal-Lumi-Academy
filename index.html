export default async function handler(req, res) {
  // CORS headers
  res.setHeader('Access-Control-Allow-Origin', '*');
  res.setHeader('Access-Control-Allow-Methods', 'POST, OPTIONS');
  res.setHeader('Access-Control-Allow-Headers', 'Content-Type');

  if (req.method === 'OPTIONS') {
    return res.status(200).end();
  }

  if (req.method !== 'POST') {
    return res.status(405).json({ error: 'Method not allowed' });
  }

  const { nome, email, telefone, crm, especialidade, prescricao, motivo } = req.body;

  // Validação básica
  if (!nome || !email || !telefone || !crm) {
    return res.status(400).json({ error: 'Campos obrigatórios não preenchidos.' });
  }

  // Mapeia valor do radio para texto legível
  const prescricaoTexto = {
    nunca: 'Nunca prescrevi',
    alguns: 'Já prescrevi em alguns casos',
    regular: 'Prescrevo regularmente',
  }[prescricao] || 'Não informado';

  // Monta o HTML do e-mail
  const htmlEmail = `
    <div style="font-family: 'Helvetica Neue', Arial, sans-serif; max-width: 600px; margin: 0 auto; background: #ffffff;">
      <div style="background: #1a3a2a; padding: 32px 28px; border-radius: 12px 12px 0 0;">
        <h1 style="margin: 0; color: #e8d48b; font-size: 22px; font-weight: 700;">Nova Inscrição — Dossiê Clínico</h1>
        <p style="margin: 6px 0 0; color: rgba(255,255,255,0.6); font-size: 14px;">Lumi Cannabis &amp; Academy</p>
      </div>

      <div style="padding: 32px 28px; border: 1px solid #e8e8e8; border-top: none; border-radius: 0 0 12px 12px;">
        <table style="width: 100%; border-collapse: collapse;">
          <tr>
            <td style="padding: 12px 0; border-bottom: 1px solid #f0f0f0; color: #888; font-size: 13px; width: 140px; vertical-align: top;">Nome</td>
            <td style="padding: 12px 0; border-bottom: 1px solid #f0f0f0; color: #1a1a1a; font-size: 15px; font-weight: 600;">${nome}</td>
          </tr>
          <tr>
            <td style="padding: 12px 0; border-bottom: 1px solid #f0f0f0; color: #888; font-size: 13px; vertical-align: top;">E-mail</td>
            <td style="padding: 12px 0; border-bottom: 1px solid #f0f0f0; color: #1a1a1a; font-size: 15px;">
              <a href="mailto:${email}" style="color: #2d5e3f; text-decoration: none;">${email}</a>
            </td>
          </tr>
          <tr>
            <td style="padding: 12px 0; border-bottom: 1px solid #f0f0f0; color: #888; font-size: 13px; vertical-align: top;">Telefone / WhatsApp</td>
            <td style="padding: 12px 0; border-bottom: 1px solid #f0f0f0; color: #1a1a1a; font-size: 15px;">
              <a href="https://wa.me/55${telefone.replace(/\D/g, '')}" style="color: #2d5e3f; text-decoration: none;">${telefone}</a>
            </td>
          </tr>
          <tr>
            <td style="padding: 12px 0; border-bottom: 1px solid #f0f0f0; color: #888; font-size: 13px; vertical-align: top;">CRM / CRO</td>
            <td style="padding: 12px 0; border-bottom: 1px solid #f0f0f0; color: #1a1a1a; font-size: 15px; font-weight: 600;">${crm}</td>
          </tr>
          <tr>
            <td style="padding: 12px 0; border-bottom: 1px solid #f0f0f0; color: #888; font-size: 13px; vertical-align: top;">Especialidade</td>
            <td style="padding: 12px 0; border-bottom: 1px solid #f0f0f0; color: #1a1a1a; font-size: 15px;">${especialidade || 'Não informada'}</td>
          </tr>
          <tr>
            <td style="padding: 12px 0; border-bottom: 1px solid #f0f0f0; color: #888; font-size: 13px; vertical-align: top;">Prescreve cannabis?</td>
            <td style="padding: 12px 0; border-bottom: 1px solid #f0f0f0; color: #1a1a1a; font-size: 15px;">
              <span style="background: #e8f5e9; color: #2d5e3f; padding: 4px 12px; border-radius: 20px; font-size: 13px; font-weight: 600;">${prescricaoTexto}</span>
            </td>
          </tr>
          ${motivo ? `
          <tr>
            <td style="padding: 12px 0; color: #888; font-size: 13px; vertical-align: top;">Motivo / Objetivos</td>
            <td style="padding: 12px 0; color: #1a1a1a; font-size: 15px; line-height: 1.6;">${motivo}</td>
          </tr>
          ` : ''}
        </table>

        <div style="margin-top: 28px; padding-top: 20px; border-top: 2px solid #e8f5e9; text-align: center;">
          <a href="mailto:${email}" style="display: inline-block; background: #c8a84e; color: #1a3a2a; padding: 12px 32px; border-radius: 100px; text-decoration: none; font-weight: 700; font-size: 14px;">Responder ${nome.split(' ')[0]}</a>
        </div>
      </div>

      <p style="text-align: center; color: #bbb; font-size: 11px; margin-top: 20px;">Enviado automaticamente pela página do Dossiê Clínico — Lumi Academy</p>
    </div>
  `;

  try {
    const response = await fetch('https://api.resend.com/emails', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        Authorization: `Bearer ${process.env.RESEND_API_KEY}`,
      },
      body: JSON.stringify({
        from: 'Lumi Academy <onboarding@resend.dev>',
        to: ['rafael.bandeira@outlook.com'],
        subject: `Nova Inscrição — ${nome} (${crm})`,
        html: htmlEmail,
        reply_to: email,
      }),
    });

    const data = await response.json();

    if (!response.ok) {
      console.error('Resend error:', data);
      return res.status(500).json({ error: 'Falha ao enviar e-mail.', details: data });
    }

    return res.status(200).json({ success: true, id: data.id });
  } catch (error) {
    console.error('Server error:', error);
    return res.status(500).json({ error: 'Erro interno do servidor.' });
  }
}
